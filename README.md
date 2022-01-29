# Azure Naming Policies

Fork from [jnmasten/blog](https://github.com/jnmasten/blog/tree/main/azure/policy/namingConvention)

Updated to match existing naming conventions.

Read more at https://jasonmasten.com/2021/02/15/enforce-your-azure-naming-convention-with-azure-policy/

## Region Names



[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjnmasten%2Fblog%2Fmain%2Fazure%2Fpolicy%2FnamingConvention%2Fpolicy.json)
[![Deploy to Azure Gov](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazuregov.svg?sanitize=true)](https://portal.azure.us/?#blade/Microsoft_Azure_Policy/CreatePolicyDefinitionBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjnmasten%2Fblog%2Fmain%2Fazure%2Fpolicy%2FnamingConvention%2Fpolicy.json)

## Try with PowerShell (replace Policy URI as needed)

````powershell

$definition = New-AzPolicyDefinition `
    -Name 'NamingStandard_VirtualMachine_Deny' `
    -DisplayName 'NamingStandard_VirtualMachine_Deny' `
    -Description 'This policy governs the naming standard for virtual machines.' `
    -Policy 'https://raw.githubusercontent.com/lekman/azpolicy/main/azure/policy/namingConvention/policy.naming.rules.json' `
    -Parameter 'https://raw.githubusercontent.com/jnmasten/blog/main/azure/policy/namingConvention/policy.parameters.json' `
    -Mode 'All' `
    -Metadata '{"category":"Governance"}'

New-AzPolicyAssignment `
    -Name '<Assignment Name>' `
    -Scope '<Scope>' `
    -Application '<Application>' `
    -Environment '<Environment Abbreviation>' `
    -DataCenterCRegion '<Data Center Region>' `
    -DataCenterLocation '<Primary Location Abbreviation>' `
    -PolicyDefinition $definition

````

## Try with CLI

````cli

az policy definition create --name 'NamingStandard_VirtualMachine_Deny' --display-name 'NamingStandard_VirtualMachine_Deny' --description 'This policy governs the naming standard for virtual machines.' --rules 'https://raw.githubusercontent.com/lekman/azpolicy/main/azure/policy/namingConvention/policy.naming.rules.json' --params 'https://raw.githubusercontent.com/jnmasten/blog/main/azure/policy/namingConvention/policy.parameters.json' --mode All

az policy assignment create --name <Assignment Name> --scope <scope> --policy "NamingStandard_VirtualMachine_Deny"
