---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394240"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: Usunięto pusty zestaw HTTPS

Zestaw <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> został usunięty.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

W ASP.NET Core 2,1 zawartość `Microsoft.AspNetCore.Server.Kestrel.Https` została przeniesiona do <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>lokalizacji. Ta zmiana została wykonana w sposób rozdzielny przy `[TypeForwardedTo]` użyciu atrybutów.

#### <a name="recommended-action"></a>Zalecana akcja

- Biblioteki, `Microsoft.AspNetCore.Server.Kestrel.Https` do których odwołuje się 2,0, powinny aktualizować wszystkie zależności ASP.NET Core do 2,1 lub nowszych. W przeciwnym razie mogą wystąpić przerwy w przypadku załadowania do aplikacji ASP.NET Core 3,0.
- Aplikacje i biblioteki ukierunkowane na ASP.NET Core 2,1 i nowsze powinny usunąć wszystkie bezpośrednie odwołania `Microsoft.AspNetCore.Server.Kestrel.Https` do pakietu NuGet.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
