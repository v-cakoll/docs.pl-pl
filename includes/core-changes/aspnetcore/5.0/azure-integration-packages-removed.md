---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416264"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure: Usunięto wstępnie ustalone pakiety integracji platformy Azure

Następujące `Microsoft.*` pakiety zapewniające integrację między ASP.NET Core i zestawami SDK platformy Azure nie są uwzględnione w ASP.NET Core 5,0:

* [Microsoft.Extensions.Configwersja. AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), która integruje [Azure Key Vault](/azure/key-vault/) do [systemu konfiguracji](/aspnet/core/fundamentals/configuration/).
* [Microsoft. AspNetCore. dataprotection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), który integruje Azure Key Vault z [ASP.NET Core systemem ochrony danych](/aspnet/core/security/data-protection/introduction).
* [Microsoft. AspNetCore. dataprotection. AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), który integruje [BLOB Storage platformy Azure](/azure/storage/blobs/) z systemem ochrony danych ASP.NET Core.

Aby zapoznać się z omówieniem tego problemu, zobacz [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 1

#### <a name="old-behavior"></a>Stare zachowanie

`Microsoft.*`Pakiety zintegrowane z usługami platformy Azure z interfejsami API konfiguracji i ochrony danych.

#### <a name="new-behavior"></a>Nowe zachowanie

Nowe `Azure.*` pakiety integrują usługi platformy Azure z interfejsami API konfiguracji i ochrony danych.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wprowadzono zmianę, ponieważ `Microsoft.*` pakiety:

* Korzystanie z nieaktualnych wersji zestawu Azure SDK. Proste aktualizacje nie były możliwe, ponieważ nowe wersje zestawu Azure SDK obejmowały istotne zmiany.
* Powiązane z harmonogramem wersji platformy .NET Core. Przeniesienie własności pakietów do zespołu zestawu Azure SDK umożliwia aktualizowanie pakietów w miarę aktualizowania zestawu Azure SDK.

#### <a name="recommended-action"></a>Zalecana akcja

W ASP.NET Core 2,1 lub nowszych projektach Zastąp stary `Microsoft.*` z nowymi `Azure.*` pakietami.

| Starsze | Nowy |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure. Extensions. AspNetCore. dataprotection. Keys](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure. Extensions. AspNetCore. dataprotection. Blobs](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.AspNetCore.Configwersja. Klucz](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

Nowe pakiety korzystają z nowej wersji zestawu Azure SDK, która zawiera istotne zmiany. Wzorce użycia ogólne nie są zmieniane. Niektóre przeciążenia i opcje mogą się różnić w zależności od zmian w bazowych interfejsach API zestawu Azure SDK.

Stare pakiety będą:

* Być obsługiwane przez zespół ASP.NET Core w okresie istnienia .NET Core 2,1 i 3,1.
* Nie jest uwzględniony w programie .NET 5.

Podczas uaktualniania projektu do programu .NET 5 Przejdź do pakietów, `Azure.*` Aby zachować pomoc techniczną.

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
