---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902001"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Ochrona danych: usługa dataprotection. AzureStorage używa nowych interfejsów API usługi Azure Storage

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>zależy od [bibliotek usługi Azure Storage](https://github.com/Azure/azure-storage-net). Te biblioteki zmieniły swoje zestawy, pakiety i przestrzenie nazw. Począwszy od ASP.NET Core 3,0, `Microsoft.AspNetCore.DataProtection.AzureStorage` program używa nowych `Microsoft.Azure.Storage.`prefiksów interfejsów API i pakietów.

Pytania dotyczące interfejsów API usługi Azure Storage można używać <https://github.com/Azure/azure-storage-net>. Aby zapoznać się z omówieniem tego problemu, zobacz [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet przywoływany `WindowsAzure.Storage` do pakietu NuGet.

#### <a name="new-behavior"></a>Nowe zachowanie

Pakiet odwołuje się `Microsoft.Azure.Storage.Blob` do pakietu NuGet.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana umożliwia `Microsoft.AspNetCore.DataProtection.AzureStorage` Migrowanie do zalecanych pakietów usługi Azure Storage.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli nadal potrzebujesz użyć starszych interfejsów API usługi Azure Storage z ASP.NET Core 3,0, Dodaj bezpośrednią zależność do pakietu [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) . Ten pakiet można zainstalować obok nowych `Microsoft.Azure.Storage` interfejsów API.

W wielu przypadkach uaktualnienie obejmuje jedynie zmianę `using` instrukcji w celu użycia nowych przestrzeni nazw:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
