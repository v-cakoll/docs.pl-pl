---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394240"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: Usunięto pusty zestaw HTTPS

Zestaw <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> został usunięty.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

W ASP.NET Core 2,1 zawartość `Microsoft.AspNetCore.Server.Kestrel.Https` została przeniesiona do <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>. Ta zmiana została wykonana w sposób rozdzielny przy użyciu atrybutów `[TypeForwardedTo]`.

#### <a name="recommended-action"></a>Zalecana akcja

- Biblioteki odwołujące się `Microsoft.AspNetCore.Server.Kestrel.Https` 2,0 powinny aktualizować wszystkie zależności ASP.NET Core do 2,1 lub nowsze. W przeciwnym razie mogą wystąpić przerwy w przypadku załadowania do aplikacji ASP.NET Core 3,0.
- Aplikacje i biblioteki ukierunkowane na ASP.NET Core 2,1 i nowsze powinny usunąć wszystkie bezpośrednie odwołania do pakietu NuGet `Microsoft.AspNetCore.Server.Kestrel.Https`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
