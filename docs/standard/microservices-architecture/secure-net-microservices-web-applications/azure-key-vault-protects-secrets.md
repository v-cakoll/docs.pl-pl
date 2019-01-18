---
title: Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji
description: Zabezpieczenia w Mikrousługach .NET i aplikacji sieci Web — usługi Azure Key Vault jest doskonałym sposobem obsługi wpisów tajnych aplikacji, które całkowicie są kontrolowane przez administratorów. Administratorzy mogą nawet przypisać i odwoływać rozwoju wartości bez konieczności je obsłużyć deweloperów.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 291d60f941e4280ff120296ce1c392df3300dc44
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362422"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="2f149-104">Użyj usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji</span><span class="sxs-lookup"><span data-stu-id="2f149-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="2f149-105">Kluczy tajnych przechowywanych jako zmienne środowiskowe ani przechowywane przez narzędzie Menedżer klucz tajny są nadal przechowywane lokalnie i niezaszyfrowanego na maszynie.</span><span class="sxs-lookup"><span data-stu-id="2f149-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="2f149-106">Opcja bardziej bezpieczna do przechowywania wpisów tajnych jest [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/), która zapewnia bezpieczny i centralną lokalizację do przechowywania kluczy i wpisów tajnych.</span><span class="sxs-lookup"><span data-stu-id="2f149-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="2f149-107">**Microsoft.Extensions.Configuration.AzureKeyVault** pakiet umożliwia aplikacji ASP.NET Core można odczytać informacji o konfiguracji z usługi Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="2f149-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="2f149-108">Aby rozpocząć korzystanie z wpisy tajne z usługi Azure Key Vault, możesz wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="2f149-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="2f149-109">Rejestruje aplikację jako aplikację usługi Azure AD.</span><span class="sxs-lookup"><span data-stu-id="2f149-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="2f149-110">(Dostęp do magazynów kluczy jest zarządzane przez usługę Azure AD). Można to zrobić za pomocą portalu zarządzania systemu Azure. \\</span><span class="sxs-lookup"><span data-stu-id="2f149-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.\\</span></span>

   <span data-ttu-id="2f149-111">Alternatywnie, jeśli chcesz, aby aplikacji w celu uwierzytelniania za pomocą certyfikatu zamiast wpisu tajnego hasła lub klienta, można użyć [New AzureRmADApplication](/powershell/module/azurerm.resources/new-azurermadapplication) polecenia cmdlet programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f149-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzureRmADApplication](/powershell/module/azurerm.resources/new-azurermadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="2f149-112">Certyfikat, który należy zarejestrować w usłudze Azure Key Vault musi tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="2f149-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="2f149-113">(Aplikacja będzie używać klucza prywatnego).</span><span class="sxs-lookup"><span data-stu-id="2f149-113">(Your application will use the private key.)</span></span>

2. <span data-ttu-id="2f149-114">Udostępnij zarejestrowanej aplikacji do magazynu kluczy, tworząc nową usługę podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2f149-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="2f149-115">Można to zrobić za pomocą następujących poleceń programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2f149-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="2f149-116">Obejmują usługi key vault jako źródło konfiguracji w aplikacji, wywołując <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> metodę rozszerzenia, tworząc <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2f149-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="2f149-117">Należy pamiętać, że wywołanie `AddAzureKeyVault` wymaga Identyfikatora aplikacji, który został zarejestrowany i biorąc pod uwagę dostępu do magazynu kluczy w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="2f149-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="2f149-118">Można również użyć przeciążenia `AddAzureKeyVault` przyjmującej certyfikatu zamiast wpisu tajnego klienta po prostu, umieszczając odwołanie do [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) pakietu.</span><span class="sxs-lookup"><span data-stu-id="2f149-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f149-119">Firma Microsoft zaleca rejestracji usługi Azure Key Vault jako ostatni dostawcę konfiguracji, aby go zastąpić wartości konfiguracji z poprzedniej dostawców.</span><span class="sxs-lookup"><span data-stu-id="2f149-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2f149-120">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="2f149-120">Additional resources</span></span>

- <span data-ttu-id="2f149-121">**Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego aplikacji** \\</span><span class="sxs-lookup"><span data-stu-id="2f149-121">**Using Azure Key Vault to protect application secrets** \\</span></span>
  [*https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault*](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="2f149-122">**Bezpieczne przechowywanie kluczy tajnych aplikacji w czasie projektowania** \\</span><span class="sxs-lookup"><span data-stu-id="2f149-122">**Safe storage of app secrets during development** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/app-secrets*](/aspnet/core/security/app-secrets)

- <span data-ttu-id="2f149-123">**Konfigurowanie ochrony danych** \\</span><span class="sxs-lookup"><span data-stu-id="2f149-123">**Configuring data protection** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview*](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="2f149-124">**Zarządzanie kluczami i okresem istnienia** \\</span><span class="sxs-lookup"><span data-stu-id="2f149-124">**Key management and lifetime** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings\#data-protection-default-settings*](/aspnet/core/security/data-protection/configuration/default-settings#data-protection-default-settings)

- <span data-ttu-id="2f149-125">**Microsoft.Extensions.Configuration.KeyPerFile** repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="2f149-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repo.</span></span> \
  [*https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile*](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
><span data-ttu-id="2f149-126">[Poprzednie](developer-app-secrets-storage.md)
>[dalej](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="2f149-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
