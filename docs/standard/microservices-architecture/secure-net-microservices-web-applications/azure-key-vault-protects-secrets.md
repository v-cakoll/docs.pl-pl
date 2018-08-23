---
title: Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 84e016e4620b73444f800b02076489012ea5e844
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752132"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji

Kluczy tajnych przechowywanych jako zmienne środowiskowe ani przechowywane przez narzędzie Menedżer klucz tajny są nadal przechowywane lokalnie i niezaszyfrowanego na maszynie. Opcja bardziej bezpieczna do przechowywania wpisów tajnych jest [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/), która zapewnia bezpieczny i centralną lokalizację do przechowywania kluczy i wpisów tajnych.

Pakiet Microsoft.Extensions.Configuration.AzureKeyVault umożliwia aplikacji platformy ASP.NET Core można odczytać informacji o konfiguracji z usługi Azure Key Vault. Aby rozpocząć korzystanie z wpisy tajne z usługi Azure Key Vault, możesz wykonaj następujące kroki:

Najpierw zarejestrować aplikację jako aplikację usługi Azure AD. (Dostęp do magazynów kluczy jest zarządzane przez usługę Azure AD). Można to zrobić za pomocą portalu zarządzania systemu Azure.

Alternatywnie, jeśli chcesz, aby aplikacji w celu uwierzytelniania za pomocą certyfikatu zamiast wpisu tajnego hasła lub klienta, można użyć [New AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) polecenia cmdlet programu PowerShell. Certyfikat, który należy zarejestrować w usłudze Azure Key Vault musi tylko klucz publiczny. (Aplikacja będzie używać klucza prywatnego).

Po drugie należy udzielić dostępu zarejestrowanej aplikacji do usługi key vault, tworząc nową jednostkę usługi. Można to zrobić za pomocą następujących poleceń programu PowerShell:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Po trzecie obejmują usługi key vault jako źródło konfiguracji w aplikacji przez wywołanie metody rozszerzenia IConfigurationBuilder.AddAzureKeyVault podczas tworzenia wystąpienia IConfigurationRoot. Należy pamiętać, że wywołanie AddAzureKeyVault będzie wymagać Identyfikatora aplikacji, który został zarejestrowany i biorąc pod uwagę dostępu do magazynu kluczy w poprzednich krokach.

  Obecnie .NET Standard i .NET Core obsługują pobieranie informacji o konfiguracji z usługi Azure Key Vault przy użyciu Identyfikatora klienta oraz klucz tajny klienta. Aplikacje programu .NET framework, można użyć przeciążenia IConfigurationBuilder.AddAzureKeyVault, która przyjmuje certyfikatu zamiast wpisu tajnego klienta. Na chwilę obecną, praca jest [w toku](https://github.com/aspnet/Configuration/issues/605) udostępnić tego przeciążenia w .NET Standard i .NET Core. Aż do przeciążenia AddAzureKeyVault, które przyjmuje się, że certyfikat jest dostępny, platformy ASP.NET Core aplikacje mają dostęp do usługi Azure Key Vault przy użyciu uwierzytelniania opartego na certyfikatach przez jawne Tworzenie obiektu KeyVaultClient, jak pokazano w poniższym przykładzie:

```csharp
// Configure Key Vault client
var kvClient = new KeyVaultClient(new KeyVaultClient.AuthenticationCallback(async
    (authority, resource, scope) =>
    {
        var cert = // Get certificate from local store/file/key vault etc. as needed
        // From the Microsoft.IdentityModel.Clients.ActiveDirectory pacakge
        var authContext = new AuthenticationContext(authority,
            TokenCache.DefaultShared);
        var result = await authContext.AcquireTokenAsync(resource,
            // From the Microsoft.Rest.ClientRuntime.Azure.Authentication pacakge
            new ClientAssertionCertificate("{Application ID}", cert));
        return result.AccessToken;
    }));

    // Get configuration values from Key Vault
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        // Other configuration providers go here.
        .AddAzureKeyVault("{KeyValueUri}", kvClient,
        new DefaultKeyVaultSecretManager());
```

W tym przykładzie wywołanie AddAzureKeyVault pochodzi z końcem rejestrację dostawcy konfiguracji. Jest najlepszym rozwiązaniem, aby zarejestrować usługi Azure Key Vault jako ostatniego dostawcę konfiguracji, tak aby mieć możliwość zastąpienia wartości konfiguracji z poprzedniej dostawców i tak, aby nie wartości konfiguracji z innych źródeł przesłaniają akcje z magazynu kluczy.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego aplikacji**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Bezpieczne przechowywanie kluczy tajnych aplikacji w czasie projektowania**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Konfigurowanie ochrony danych**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Zarządzanie kluczami i okresem istnienia**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** Repozytorium GitHub.
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Poprzednie](developer-app-secrets-storage.md)
[dalej](../key-takeaways.md)
