---
title: Korzystanie z usługi Azure Key Vault w celu ochrony kluczy tajnych w czasie tworzenia
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — usługa Azure Key Vault to doskonały sposób obsługi kluczy tajnych aplikacji, które są całkowicie kontrolowane przez administratorów. Administratorzy mogą nawet przypisywać i odwoływać wartości programistyczne bez konieczności obsługi przez deweloperów.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: cc95d491136c945255408cec2bd49d4d6579e29a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501750"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="00b3c-104">Ochrona kluczy tajnych w czasie produkcji za pomocą usługi Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="00b3c-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="00b3c-105">Wpisy tajne przechowywane jako zmienne środowiskowe lub przechowywane przez narzędzie Secret Manager są nadal przechowywane lokalnie i nieszyfrowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="00b3c-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="00b3c-106">Bezpieczniejszą opcją przechowywania kluczy tajnych jest [usługa Azure Key Vault,](https://azure.microsoft.com/services/key-vault/)która zapewnia bezpieczną, centralną lokalizację do przechowywania kluczy i kluczy tajnych.</span><span class="sxs-lookup"><span data-stu-id="00b3c-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="00b3c-107">Pakiet **Microsoft.Extensions.Configuration.AzureKeyVault** umożliwia ASP.NET aplikacji Core odczytywanie informacji o konfiguracji z usługi Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="00b3c-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="00b3c-108">Aby rozpocząć korzystanie z kluczy tajnych z usługi Azure Key Vault, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="00b3c-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="00b3c-109">Zarejestruj aplikację jako aplikację usługi Azure AD.</span><span class="sxs-lookup"><span data-stu-id="00b3c-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="00b3c-110">(Dostęp do magazynów kluczy jest zarządzany przez usługę Azure AD). Można to zrobić za pośrednictwem portalu zarządzania platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="00b3c-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>\

   <span data-ttu-id="00b3c-111">Alternatywnie, jeśli aplikacja ma uwierzytelniać przy użyciu certyfikatu zamiast hasła lub klucza tajnego klienta, możesz użyć polecenia cmdlet [programu New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00b3c-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="00b3c-112">Certyfikat zarejestrowany w usłudze Azure Key Vault wymaga tylko klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="00b3c-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="00b3c-113">Aplikacja użyje klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="00b3c-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="00b3c-114">Nadaj zarejestrowanej aplikacji dostęp do magazynu kluczy, tworząc nową jednostki usługi.</span><span class="sxs-lookup"><span data-stu-id="00b3c-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="00b3c-115">Można to zrobić za pomocą następujących poleceń programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="00b3c-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="00b3c-116">Dołącz magazyn kluczy jako źródło konfiguracji w <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> aplikacji, wywołując <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> metodę rozszerzenia podczas tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="00b3c-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="00b3c-117">Należy zauważyć, że wywołanie `AddAzureKeyVault` wymaga identyfikatora aplikacji, który został zarejestrowany i uzyskał dostęp do magazynu kluczy w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="00b3c-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="00b3c-118">Można również użyć `AddAzureKeyVault` przeciążenia, które ma certyfikat zamiast klucza tajnego klienta, po prostu dołączając odwołanie do pakietu [Microsoft.IdentityModel.Clients.ActiveDirectory.](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory)</span><span class="sxs-lookup"><span data-stu-id="00b3c-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00b3c-119">Zaleca się zarejestrowanie usługi Azure Key Vault jako ostatniego dostawcy konfiguracji, aby można było zastąpić wartości konfiguracji od poprzednich dostawców.</span><span class="sxs-lookup"><span data-stu-id="00b3c-119">We recommend that you register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="00b3c-120">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="00b3c-120">Additional resources</span></span>

- <span data-ttu-id="00b3c-121">**Korzystanie z usługi Azure Key Vault do ochrony kluczy tajnych aplikacji** </span><span class="sxs-lookup"><span data-stu-id="00b3c-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="00b3c-122">**Bezpieczne przechowywanie tajemnic aplikacji podczas tworzenia aplikacji** </span><span class="sxs-lookup"><span data-stu-id="00b3c-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="00b3c-123">**Konfigurowanie ochrony danych** </span><span class="sxs-lookup"><span data-stu-id="00b3c-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="00b3c-124">**Zarządzanie kluczami ochrony danych i okres eksploatacji w ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="00b3c-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="00b3c-125">**Repozytorium GitHub firmy Microsoft.Extensions.Configuration.KeyPerFile.**</span><span class="sxs-lookup"><span data-stu-id="00b3c-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="00b3c-126">[Poprzedni](developer-app-secrets-storage.md)
>[następny](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="00b3c-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
