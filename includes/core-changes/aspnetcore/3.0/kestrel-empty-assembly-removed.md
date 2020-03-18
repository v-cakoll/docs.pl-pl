---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394240"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Pusstrel: Usunięto pusty zespół HTTPS

Zespół <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> został usunięty.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

W ASP.NET Core 2.1 zawartość `Microsoft.AspNetCore.Server.Kestrel.Https` została <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>przeniesiona do . Ta zmiana została wykonana w sposób `[TypeForwardedTo]` nieprzerywany przy użyciu atrybutów.

#### <a name="recommended-action"></a>Zalecana akcja

- Biblioteki odwołujące `Microsoft.AspNetCore.Server.Kestrel.Https` się do wersji 2.0 powinny zaktualizować wszystkie ASP.NET zależności rdzenia do wersji 2.1 lub nowszej. W przeciwnym razie mogą się zepsuć po załadowaniu do ASP.NET aplikacji Core 3.0.
- Aplikacje i biblioteki przeznaczone ASP.NET Core 2.1 i `Microsoft.AspNetCore.Server.Kestrel.Https` nowszej powinny usunąć wszelkie bezpośrednie odwołania do pakietu NuGet.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
