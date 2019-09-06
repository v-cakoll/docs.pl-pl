---
title: Korzystanie z usługi Azure Key Vault w celu ochrony kluczy tajnych w czasie tworzenia
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — Azure Key Vault jest doskonałym sposobem obsługi wpisów tajnych aplikacji, które są w pełni kontrolowane przez administratorów. Administratorzy mogą nawet przypisywać i odwoływać wartości deweloperskie bez deweloperów, którzy muszą je obsłużyć.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 63bf357c95b82a820b6dfb6a2d24a5d89f66de72
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296479"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="3d699-104">Użyj Azure Key Vault, aby chronić wpisy tajne w czasie produkcji</span><span class="sxs-lookup"><span data-stu-id="3d699-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="3d699-105">Wpisy tajne przechowywane jako zmienne środowiskowe lub przechowywane przez narzędzie tajnego Menedżera są nadal przechowywane lokalnie i niezaszyfrowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3d699-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="3d699-106">Bezpieczniejszym rozwiązaniem do przechowywania wpisów tajnych jest [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), które zapewnia bezpieczną, centralną lokalizację do przechowywania kluczy i wpisów tajnych.</span><span class="sxs-lookup"><span data-stu-id="3d699-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="3d699-107">Pakiet **Microsoft. Extensions. Configuration. AzureKeyVault** umożliwia aplikacji ASP.NET Core odczytywanie informacji o konfiguracji z Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="3d699-107">The **Microsoft.Extensions.Configuration.AzureKeyVault** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="3d699-108">Aby rozpocząć korzystanie z wpisów tajnych z Azure Key Vault, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3d699-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="3d699-109">Zarejestruj swoją aplikację jako aplikację usługi Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3d699-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="3d699-110">(Dostęp do magazynów kluczy jest zarządzany przez usługę Azure AD). Można to zrobić za pomocą portalu zarządzania systemu Azure.</span><span class="sxs-lookup"><span data-stu-id="3d699-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.\</span></span>

   <span data-ttu-id="3d699-111">Alternatywnie, jeśli aplikacja ma być uwierzytelniana przy użyciu certyfikatu zamiast hasła lub klucza tajnego klienta, można użyć polecenia cmdlet [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3d699-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="3d699-112">Certyfikat rejestrowany przy użyciu Azure Key Vault wymaga tylko klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3d699-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="3d699-113">Twoja aplikacja będzie używać klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="3d699-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="3d699-114">Nadaj zarejestrowanej aplikacji dostęp do magazynu kluczy, tworząc nową nazwę główną usługi.</span><span class="sxs-lookup"><span data-stu-id="3d699-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="3d699-115">Można to zrobić za pomocą następujących poleceń programu PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3d699-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="3d699-116">Dołącz Magazyn kluczy jako źródło konfiguracji w aplikacji przez wywołanie <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> metody rozszerzenia podczas <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3d699-116">Include the key vault as a configuration source in your application by calling the <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span> <span data-ttu-id="3d699-117">Należy zauważyć, `AddAzureKeyVault` że wywołanie wymaga identyfikatora aplikacji, który został zarejestrowany i ma dostęp do magazynu kluczy w poprzednich krokach.</span><span class="sxs-lookup"><span data-stu-id="3d699-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span>

   <span data-ttu-id="3d699-118">Można również użyć przeciążenia `AddAzureKeyVault` , które ma certyfikat zamiast klucza tajnego klienta, tylko dołączając odwołanie do pakietu [Microsoft. IdentityModel. clients. ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) .</span><span class="sxs-lookup"><span data-stu-id="3d699-118">You can also use an overload of `AddAzureKeyVault` that takes a certificate in place of the client secret by just including a reference to the [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) package.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d699-119">Zalecamy zarejestrowanie Azure Key Vault jako ostatni dostawca konfiguracji, aby można było zastąpić wartości konfiguracji od poprzednich dostawców.</span><span class="sxs-lookup"><span data-stu-id="3d699-119">We recommend you to register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3d699-120">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="3d699-120">Additional resources</span></span>

- <span data-ttu-id="3d699-121">**Ochrona wpisów tajnych aplikacji przy użyciu Azure Key Vault** </span><span class="sxs-lookup"><span data-stu-id="3d699-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- <span data-ttu-id="3d699-122">**Bezpieczne przechowywanie wpisów tajnych aplikacji podczas opracowywania** </span><span class="sxs-lookup"><span data-stu-id="3d699-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="3d699-123">**Konfigurowanie ochrony danych** </span><span class="sxs-lookup"><span data-stu-id="3d699-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="3d699-124">**Zarządzanie kluczami i okres istnienia ochrony danych w ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="3d699-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- <span data-ttu-id="3d699-125">Repozytorium GitHub **Microsoft. Extensions. Configuration. KeyPerFile** .</span><span class="sxs-lookup"><span data-stu-id="3d699-125">**Microsoft.Extensions.Configuration.KeyPerFile** GitHub repository.</span></span> \
  <https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile>

>[!div class="step-by-step"]
><span data-ttu-id="3d699-126">[Poprzedni](developer-app-secrets-storage.md)Następny
>[](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="3d699-126">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
