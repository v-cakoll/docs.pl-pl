---
title: Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: cbe893dcdd71f0ce8bf8a26a8502d6c0b3a0dedb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151151"
---
# <a name="using-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="9b12b-103">Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji</span><span class="sxs-lookup"><span data-stu-id="9b12b-103">Using Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="9b12b-104">Kluczy tajnych przechowywanych jako zmienne środowiskowe ani przechowywane przez narzędzie Menedżer klucz tajny są nadal przechowywane lokalnie i niezaszyfrowanego na maszynie.</span><span class="sxs-lookup"><span data-stu-id="9b12b-104">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="9b12b-105">Opcja bardziej bezpieczna do przechowywania wpisów tajnych jest [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/), która zapewnia bezpieczny i centralną lokalizację do przechowywania kluczy i wpisów tajnych.</span><span class="sxs-lookup"><span data-stu-id="9b12b-105">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="9b12b-106">Pakiet Microsoft.Extensions.Configuration.AzureKeyVault umożliwia aplikacji platformy ASP.NET Core można odczytać informacji o konfiguracji z usługi Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="9b12b-106">The Microsoft.Extensions.Configuration.AzureKeyVault package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="9b12b-107">Aby rozpocząć korzystanie z wpisy tajne z usługi Azure Key Vault, możesz wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9b12b-107">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

<span data-ttu-id="9b12b-108">Najpierw zarejestrować aplikację jako aplikację usługi Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9b12b-108">First, register your application as an Azure AD application.</span></span> <span data-ttu-id="9b12b-109">(Dostęp do magazynów kluczy jest zarządzane przez usługę Azure AD). Można to zrobić za pomocą portalu zarządzania systemu Azure.</span><span class="sxs-lookup"><span data-stu-id="9b12b-109">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>

<span data-ttu-id="9b12b-110">Alternatywnie, jeśli chcesz, aby aplikacji w celu uwierzytelniania za pomocą certyfikatu zamiast wpisu tajnego hasła lub klienta, można użyć [New AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) polecenia cmdlet programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b12b-110">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](https://docs.microsoft.com/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="9b12b-111">Certyfikat, który należy zarejestrować w usłudze Azure Key Vault musi tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="9b12b-111">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="9b12b-112">(Aplikacja będzie używać klucza prywatnego).</span><span class="sxs-lookup"><span data-stu-id="9b12b-112">(Your application will use the private key.)</span></span>

<span data-ttu-id="9b12b-113">Po drugie należy udzielić dostępu zarejestrowanej aplikacji do usługi key vault, tworząc nową jednostkę usługi.</span><span class="sxs-lookup"><span data-stu-id="9b12b-113">Second, give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="9b12b-114">Można to zrobić za pomocą następujących poleceń programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9b12b-114">You can do this using the following PowerShell commands:</span></span>

```powershell
$sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
```

<span data-ttu-id="9b12b-115">Po trzecie obejmują usługi key vault jako źródło konfiguracji w aplikacji przez wywołanie metody rozszerzenia IConfigurationBuilder.AddAzureKeyVault podczas tworzenia wystąpienia IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="9b12b-115">Third, include the key vault as a configuration source in your application by calling the IConfigurationBuilder.AddAzureKeyVault extension method when you create an IConfigurationRoot instance.</span></span> <span data-ttu-id="9b12b-116">Należy pamiętać, że wywołanie AddAzureKeyVault będzie wymagać Identyfikatora aplikacji, który został zarejestrowany i biorąc pod uwagę dostępu do magazynu kluczy w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="9b12b-116">Note that calling AddAzureKeyVault will require the application ID that was registered and given access to the key vault in the previous steps.</span></span>

  <span data-ttu-id="9b12b-117">Obecnie .NET Standard i .NET Core obsługują pobieranie informacji o konfiguracji z usługi Azure Key Vault przy użyciu Identyfikatora klienta oraz klucz tajny klienta.</span><span class="sxs-lookup"><span data-stu-id="9b12b-117">Currently, .NET Standard and .NET Core support getting configuration information from an Azure Key Vault using a client ID and client secret.</span></span> <span data-ttu-id="9b12b-118">Aplikacje programu .NET framework, można użyć przeciążenia IConfigurationBuilder.AddAzureKeyVault, która przyjmuje certyfikatu zamiast wpisu tajnego klienta.</span><span class="sxs-lookup"><span data-stu-id="9b12b-118">.NET Framework applications can use an overload of IConfigurationBuilder.AddAzureKeyVault that takes a certificate in place of the client secret.</span></span> <span data-ttu-id="9b12b-119">Na chwilę obecną, praca jest [w toku](https://github.com/aspnet/Configuration/issues/605) udostępnić tego przeciążenia w .NET Standard i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b12b-119">As of this writing, work is [in progress](https://github.com/aspnet/Configuration/issues/605) to make that overload available in .NET Standard and .NET Core.</span></span> <span data-ttu-id="9b12b-120">Aż do przeciążenia AddAzureKeyVault, które przyjmuje się, że certyfikat jest dostępny, platformy ASP.NET Core aplikacje mają dostęp do usługi Azure Key Vault przy użyciu uwierzytelniania opartego na certyfikatach przez jawne Tworzenie obiektu KeyVaultClient, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b12b-120">Until the AddAzureKeyVault overload that accepts a certificate is available, ASP.NET Core applications can access an Azure Key Vault with certificate-based authentication by explicitly creating a KeyVaultClient object, as shown in the following example:</span></span>

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

<span data-ttu-id="9b12b-121">W tym przykładzie wywołanie AddAzureKeyVault pochodzi z końcem rejestrację dostawcy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9b12b-121">In this example, the call to AddAzureKeyVault comes at the end of configuration provider registration.</span></span> <span data-ttu-id="9b12b-122">Jest najlepszym rozwiązaniem, aby zarejestrować usługi Azure Key Vault jako ostatniego dostawcę konfiguracji, tak aby mieć możliwość zastąpienia wartości konfiguracji z poprzedniej dostawców i tak, aby nie wartości konfiguracji z innych źródeł przesłaniają akcje z magazynu kluczy.</span><span class="sxs-lookup"><span data-stu-id="9b12b-122">It is a best practice to register Azure Key Vault as the last configuration provider so that it has an opportunity to override configuration values from previous providers, and so that no configuration values from other sources override those from the key vault.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9b12b-123">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9b12b-123">Additional resources</span></span>

-   <span data-ttu-id="9b12b-124">**Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego aplikacji**
    [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span><span class="sxs-lookup"><span data-stu-id="9b12b-124">**Using Azure Key Vault to protect application secrets**
[*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault)</span></span>

-   <span data-ttu-id="9b12b-125">**Bezpieczne przechowywanie kluczy tajnych aplikacji w czasie projektowania**
    [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="9b12b-125">**Safe storage of app secrets during development**
[*https://docs.microsoft.com/aspnet/core/security/app-secrets*](https://docs.microsoft.com/aspnet/core/security/app-secrets)</span></span>

-   <span data-ttu-id="9b12b-126">**Konfigurowanie ochrony danych**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span><span class="sxs-lookup"><span data-stu-id="9b12b-126">**Configuring data protection**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview)</span></span>

-   <span data-ttu-id="9b12b-127">**Zarządzanie kluczami i okresem istnienia**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span><span class="sxs-lookup"><span data-stu-id="9b12b-127">**Key management and lifetime**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)</span></span>

-   <span data-ttu-id="9b12b-128">**Microsoft.Extensions.Configuration.KeyPerFile** repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="9b12b-128">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repo.</span></span>
    [*https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile*](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
><span data-ttu-id="9b12b-129">[Poprzednie](developer-app-secrets-storage.md)
>[dalej](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="9b12b-129">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>