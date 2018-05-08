---
title: Ochrona kluczy tajnych w czasie produkcji za pomocą usługi Azure Key Vault
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Ochrona kluczy tajnych w czasie produkcji za pomocą usługi Azure Key Vault
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 5ad5686909c29eba5916cbcc4b7115a16108a004
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a>Ochrona kluczy tajnych w czasie produkcji za pomocą usługi Azure Key Vault

Klucze tajne przechowywanych jako zmienne środowiskowe ani przechowywane przez narzędzie Menedżer klucz tajny są nadal przechowywane lokalnie i bez szyfrowania na komputerze. Opcja bardziej bezpieczna do przechowywania kluczy tajnych jest [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/), która zapewnia bezpieczny, centralną lokalizację do przechowywania kluczy i kluczy tajnych.

Pakiet Microsoft.Extensions.Configuration.AzureKeyVault umożliwia aplikacji platformy ASP.NET Core odczytu informacji o konfiguracji z usługą Azure Key Vault. Aby rozpocząć korzystanie z kluczy tajnych z usługi Azure Key Vault, możesz wykonaj następujące kroki:

Najpierw zarejestrować aplikację jako aplikację usługi Azure AD. (Dostęp do magazynów kluczy jest zarządzane przez usługę Azure AD). Można to zrobić za pomocą portalu zarządzania Azure.

Jeśli chcesz, aby aplikacja do uwierzytelniania za pomocą certyfikatu zamiast klucza tajnego klienta lub hasło, możesz też użyć [AzureRmADApplication nowy](https://docs.microsoft.com/powershell/resourcemanager/azurerm.resources/v3.3.0/new-azurermadapplication) polecenia cmdlet programu PowerShell. Certyfikat, który możesz zarejestrować w usłudze Azure Key Vault musi tylko klucz publiczny. (Aplikacja będzie używać klucza prywatnego.)

Po drugie zapewniają dostęp zarejestrowaną aplikację do magazynu kluczy, tworząc nową główną nazwę usługi. Można to zrobić za pomocą następujących poleceń programu PowerShell:

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

Trzecie obejmują magazynu kluczy jako źródło konfiguracji w aplikacji, podczas tworzenia wystąpienia IConfigurationRoot, wywołując metodę rozszerzenie IConfigurationBuilder.AddAzureKeyVault. Należy pamiętać, że wywołanie AddAzureKeyVault będzie wymagać identyfikator aplikacji, który został zarejestrowany i uzyskać dostęp do magazynu kluczy w poprzednich krokach.

  Obecnie .NET Standard i .NET Core obsługują pobierania informacji o konfiguracji z usługą Azure Key Vault przy użyciu Identyfikatora klienta i klucz tajny klienta. Aplikacje .NET framework mogą używać przeciążenia IConfigurationBuilder.AddAzureKeyVault pobierającej certyfikatu zamiast klucza tajnego klienta. Opracowywania tego tekstu jest pracy [w toku](https://github.com/aspnet/Configuration/issues/605) udostępnić tego przeciążenia w .NET Standard i .NET Core. Do przeciążenia AddAzureKeyVault, który przyjmuje się, że certyfikat jest dostępny, platformy ASP.NET Core aplikacje mają dostęp do usługi Azure Key Vault przy użyciu uwierzytelniania opartego na certyfikatach przez jawne utworzenie obiektu KeyVaultClient, jak pokazano w poniższym przykładzie:

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

W tym przykładzie wywołanie AddAzureKeyVault pochodzi z końcem okresu rejestrację dostawcy konfiguracji. Jest najlepszym rozwiązaniem, aby zarejestrować usługi Azure Key Vault jako ostatniego dostawcę konfiguracji, aby miała możliwość zastąpienia wartości konfiguracji z poprzedniej dostawcy, a nie wartości konfiguracji z innych źródeł, przesłaniają akcje z magazynu kluczy.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Ochrona kluczy tajnych aplikacji za pomocą usługi Azure Key Vault**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)

-   **Bezpieczne przechowywanie klucze tajne aplikacji w czasie projektowania**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)

-   **Konfigurowanie ochrony danych**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)

-   **Klucz zarządzania i okresem istnienia**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#— ustawienia ochrony danych domyślna*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

-   **Microsoft.Extensions.Configuration.DockerSecrets.** Repozytorium GitHub.
    [*https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets*](https://github.com/aspnet/Configuration/tree/dev/src/Microsoft.Extensions.Configuration.DockerSecrets)

>[!div class="step-by-step"]
[Poprzednie] (developer-app-kluczy tajnych storage.md) [dalej] (.. / takeaways.md klucza)
