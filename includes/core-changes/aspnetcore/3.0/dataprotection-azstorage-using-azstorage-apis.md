---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394086"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Ochrona danych: usługa dataprotection. AzureStorage używa nowych interfejsów API usługi Azure Storage

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> zależy od [bibliotek usługi Azure Storage](https://github.com/Azure/azure-storage-net). Te biblioteki zmieniły swoje zestawy, pakiety i przestrzenie nazw. Począwszy od ASP.NET Core 3,0, `Microsoft.AspNetCore.DataProtection.AzureStorage` używa nowych wstępnie ustalonych `Microsoft.Azure.Storage.`interfejsów API i pakietów.

Aby uzyskać pytania dotyczące interfejsów API usługi Azure Storage, użyj <https://github.com/Azure/azure-storage-net>. Aby zapoznać się z omówieniem tego problemu, zobacz [ASPNET/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet przywoływany przez pakiet NuGet `WindowsAzure.Storage`.

#### <a name="new-behavior"></a>Nowe zachowanie

Pakiet odwołuje się do pakietu NuGet `Microsoft.Azure.Storage.Blob`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana umożliwia `Microsoft.AspNetCore.DataProtection.AzureStorage` migracji do zalecanych pakietów usługi Azure Storage.

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli nadal potrzebujesz użyć starszych interfejsów API usługi Azure Storage z ASP.NET Core 3,0, Dodaj bezpośrednią zależność do pakietu [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) . Ten pakiet można zainstalować obok nowych interfejsów API `Microsoft.Azure.Storage`.

W wielu przypadkach uaktualnienie obejmuje jedynie zmianę instrukcji `using`, tak aby korzystały z nowych przestrzeni nazw:

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
