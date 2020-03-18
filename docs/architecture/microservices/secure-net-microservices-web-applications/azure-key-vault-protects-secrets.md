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
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Ochrona kluczy tajnych w czasie produkcji za pomocą usługi Azure Key Vault

Wpisy tajne przechowywane jako zmienne środowiskowe lub przechowywane przez narzędzie Secret Manager są nadal przechowywane lokalnie i nieszyfrowane na komputerze. Bezpieczniejszą opcją przechowywania kluczy tajnych jest [usługa Azure Key Vault,](https://azure.microsoft.com/services/key-vault/)która zapewnia bezpieczną, centralną lokalizację do przechowywania kluczy i kluczy tajnych.

Pakiet **Microsoft.Extensions.Configuration.AzureKeyVault** umożliwia ASP.NET aplikacji Core odczytywanie informacji o konfiguracji z usługi Azure Key Vault. Aby rozpocząć korzystanie z kluczy tajnych z usługi Azure Key Vault, wykonaj następujące kroki:

1. Zarejestruj aplikację jako aplikację usługi Azure AD. (Dostęp do magazynów kluczy jest zarządzany przez usługę Azure AD). Można to zrobić za pośrednictwem portalu zarządzania platformy Azure.\

   Alternatywnie, jeśli aplikacja ma uwierzytelniać przy użyciu certyfikatu zamiast hasła lub klucza tajnego klienta, możesz użyć polecenia cmdlet [programu New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell. Certyfikat zarejestrowany w usłudze Azure Key Vault wymaga tylko klucza publicznego. Aplikacja użyje klucza prywatnego.

2. Nadaj zarejestrowanej aplikacji dostęp do magazynu kluczy, tworząc nową jednostki usługi. Można to zrobić za pomocą następujących poleceń programu PowerShell:

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Dołącz magazyn kluczy jako źródło konfiguracji w <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> aplikacji, wywołując <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> metodę rozszerzenia podczas tworzenia wystąpienia. Należy zauważyć, że wywołanie `AddAzureKeyVault` wymaga identyfikatora aplikacji, który został zarejestrowany i uzyskał dostęp do magazynu kluczy w poprzednich krokach.

   Można również użyć `AddAzureKeyVault` przeciążenia, które ma certyfikat zamiast klucza tajnego klienta, po prostu dołączając odwołanie do pakietu [Microsoft.IdentityModel.Clients.ActiveDirectory.](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory)

> [!IMPORTANT]
> Zaleca się zarejestrowanie usługi Azure Key Vault jako ostatniego dostawcy konfiguracji, aby można było zastąpić wartości konfiguracji od poprzednich dostawców.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Korzystanie z usługi Azure Key Vault do ochrony kluczy tajnych aplikacji** \
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Bezpieczne przechowywanie tajemnic aplikacji podczas tworzenia aplikacji** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Konfigurowanie ochrony danych** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **Zarządzanie kluczami ochrony danych i okres eksploatacji w ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- **Repozytorium GitHub firmy Microsoft.Extensions.Configuration.KeyPerFile.** \
  <https://github.com/dotnet/extensions/tree/master/src/Configuration/Config.KeyPerFile>

>[!div class="step-by-step"]
>[Poprzedni](developer-app-secrets-storage.md)
>[następny](../key-takeaways.md)
