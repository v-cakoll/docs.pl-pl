---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394187"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: Usunięto karty połączeń

W ramach przenoszenia do przenoszenia interfejsów API "pubternal" do `public` koncepcji `IConnectionAdapter` zostały usunięte z Kestrel. Karty połączeń są zastępowane przez oprogramowanie pośredniczące połączenia (podobne do oprogramowania pośredniczącego HTTP w potoku ASP.NET Core, ale w przypadku połączeń niższego poziomu). Rejestrowanie protokołu HTTPS i połączeń zostało przeniesione z kart połączeń do oprogramowania pośredniczącego połączenia. Te metody rozszerzające powinny nadal bezproblemowo współpracować, ale szczegóły implementacji zostały zmienione.

Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412). W przypadku dyskusji zobacz [ASPNET/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Składniki rozszerzalności Kestrel zostały utworzone przy użyciu `IConnectionAdapter`.

#### <a name="new-behavior"></a>Nowe zachowanie

Składniki rozszerzalności Kestrel są tworzone jako [oprogramowanie pośredniczące](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana ma na celu zapewnienie bardziej elastycznej architektury rozszerzalności.

#### <a name="recommended-action"></a>Zalecana akcja

Przekonwertuj wszelkie implementacje `IConnectionAdapter`, aby użyć nowego wzorca pośredniczącego, jak pokazano [poniżej](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
