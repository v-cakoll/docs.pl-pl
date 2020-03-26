---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291632"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Platforma Azure: usunięto pakiety integracji platformy Azure z prefiksem platformy Microsoft

Następujące `Microsoft.*` pakiety, które zapewniają integrację między ASP.NET Core i Azure SDK nie są zawarte w ASP.NET Core 5.0:

* [Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), który integruje [usługę Azure Key Vault](/azure/key-vault/) z systemem [konfiguracji](/aspnet/core/fundamentals/configuration/).
* [Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), który integruje usługę Azure Key Vault z [ASP.NET core data protection system](/aspnet/core/security/data-protection/introduction).
* [Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), który integruje [usługę Azure Blob Storage](/azure/storage/blobs/) z ASP.NET podstawowym systemem ochrony danych.

Aby do dyskusji na ten temat, zobacz [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Wprowadzono wersję

5.0 Wersja zapoznawcza 1

#### <a name="old-behavior"></a>Stare zachowanie

Pakiety `Microsoft.*` zintegrowane usługi platformy Azure z interfejsów API konfiguracji i ochrony danych.

#### <a name="new-behavior"></a>Nowe zachowanie

Nowe `Azure.*` pakiety integrują usługi platformy Azure z interfejsami API konfiguracji i ochrony danych.

#### <a name="reason-for-change"></a>Powód zmiany

Zmiana została wniesiena, ponieważ pakiety `Microsoft.*` były:

* Przy użyciu przestarzałych wersji narzędzia Azure SDK. Proste aktualizacje nie były możliwe, ponieważ nowe wersje zestawu SDK platformy Azure zawierały zmiany wyłudania informacji.
* Powiązany z harmonogramem wydania .NET Core. Przeniesienie własności pakietów do zespołu zestawu Azure SDK umożliwia aktualizacje pakietów w miarę aktualizowannia zestawu Azure SDK.

#### <a name="recommended-action"></a>Zalecana akcja

W ASP.NET projektów Core 2.1 lub nowszych, zastąp stare `Microsoft.*` nowymi `Azure.*` pakietami.

| Stary | Nowa |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Usługa Azure.AspNetCore.DataProtection.Keys](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Obiekty blob Azure.AspNetCore.DataProtection.Blob](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Usługi Azure.Extensions.Configuration.Secrets](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

Nowe pakiety używają nowej wersji zestawu SDK platformy Azure, która zawiera przełomowe zmiany. Ogólne wzorce użycia pozostają niezmienione. Niektóre przeciążenia i opcje mogą się różnić, aby dostosować się do zmian w podstawowych interfejsach API zestawów SDK platformy Azure.

Stare pakiety będą:

* Bądź obsługiwany przez zespół ASP.NET Core przez cały okres istnienia .NET Core 2.1 i 3.1.
* Nie należy uwzględniać w .NET 5.

Podczas uaktualniania projektu do platformy .NET `Azure.*` 5, przejście do pakietów w celu utrzymania obsługi.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
