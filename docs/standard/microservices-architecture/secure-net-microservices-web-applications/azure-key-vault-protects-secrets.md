---
title: Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji
description: Zabezpieczenia w Mikrousługach .NET i aplikacji sieci Web — usługi Azure Key Vault jest doskonałym sposobem obsługi wpisów tajnych aplikacji, które całkowicie są kontrolowane przez administratorów. Administratorzy mogą nawet przypisać i odwoływać rozwoju wartości bez konieczności je obsłużyć deweloperów.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 99049dca3d127f82ba5312c94d5246940bb71ba8
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466130"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a>Użyj usługi Azure Key Vault do ochrony wpisu tajnego w czasie produkcji

Kluczy tajnych przechowywanych jako zmienne środowiskowe ani przechowywane przez narzędzie Menedżer klucz tajny są nadal przechowywane lokalnie i niezaszyfrowanego na maszynie. Opcja bardziej bezpieczna do przechowywania wpisów tajnych jest [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/), która zapewnia bezpieczny i centralną lokalizację do przechowywania kluczy i wpisów tajnych.

**Microsoft.Extensions.Configuration.AzureKeyVault** pakiet umożliwia aplikacji ASP.NET Core można odczytać informacji o konfiguracji z usługi Azure Key Vault. Aby rozpocząć korzystanie z wpisy tajne z usługi Azure Key Vault, możesz wykonaj następujące kroki:

1. Rejestruje aplikację jako aplikację usługi Azure AD. (Dostęp do magazynów kluczy jest zarządzane przez usługę Azure AD). Można to zrobić za pomocą portalu zarządzania systemu Azure. \

   Alternatywnie, jeśli chcesz, aby aplikacji w celu uwierzytelniania za pomocą certyfikatu zamiast wpisu tajnego hasła lub klienta, można użyć [New AzureRmADApplication](/powershell/module/azurerm.resources/new-azurermadapplication) polecenia cmdlet programu PowerShell. Certyfikat, który należy zarejestrować w usłudze Azure Key Vault musi tylko klucz publiczny. (Aplikacja będzie używać klucza prywatnego).

2. Udostępnij zarejestrowanej aplikacji do magazynu kluczy, tworząc nową usługę podmiotu zabezpieczeń. Można to zrobić za pomocą następujących poleceń programu PowerShell:

   ```powershell
   $sp = New-AzureRmADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzureRmKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. Obejmują usługi key vault jako źródło konfiguracji w aplikacji, wywołując <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType> metodę rozszerzenia, tworząc <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> wystąpienia. Należy pamiętać, że wywołanie `AddAzureKeyVault` wymaga Identyfikatora aplikacji, który został zarejestrowany i biorąc pod uwagę dostępu do magazynu kluczy w poprzednich krokach.

   Można również użyć przeciążenia `AddAzureKeyVault` przyjmującej certyfikatu zamiast wpisu tajnego klienta po prostu, umieszczając odwołanie do [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) pakietu.

> [!IMPORTANT]
> Firma Microsoft zaleca rejestracji usługi Azure Key Vault jako ostatni dostawcę konfiguracji, aby go zastąpić wartości konfiguracji z poprzedniej dostawców.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Za pomocą usługi Azure Key Vault do ochrony wpisu tajnego aplikacji** \
  [https://docs.microsoft.com/azure/guidance/guidance-multitenant-identity-keyvault](/azure/guidance/guidance-multitenant-identity-keyvault)

- **Bezpieczne przechowywanie kluczy tajnych aplikacji w czasie projektowania** \
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- **Konfigurowanie ochrony danych** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- **Zarządzanie kluczami ochrony danych i okres istnienia w programie ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

- **Microsoft.Extensions.Configuration.KeyPerFile** repozytorium GitHub. \
  [https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile](https://github.com/aspnet/Configuration/tree/master/src/Config.KeyPerFile)

>[!div class="step-by-step"]
>[Poprzednie](developer-app-secrets-storage.md)
>[dalej](../key-takeaways.md)
