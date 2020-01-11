---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902038"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: Usunięto karty połączeń

W ramach przenoszenia, aby przenieść interfejsy API "pubternal" do `public`, koncepcja `IConnectionAdapter` została usunięta z Kestrel. Karty połączeń są zastępowane przez oprogramowanie pośredniczące połączenia (podobne do oprogramowania pośredniczącego HTTP w potoku ASP.NET Core, ale w przypadku połączeń niższego poziomu). Rejestrowanie protokołu HTTPS i połączeń zostało przeniesione z kart połączeń do oprogramowania pośredniczącego połączenia. Te metody rozszerzające powinny nadal bezproblemowo współpracować, ale szczegóły implementacji zostały zmienione.

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412). Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Składniki rozszerzalności Kestrel zostały utworzone przy użyciu `IConnectionAdapter`.

#### <a name="new-behavior"></a>Nowe zachowanie

Składniki rozszerzalności Kestrel są tworzone jako [oprogramowanie pośredniczące](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana ma na celu zapewnienie bardziej elastycznej architektury rozszerzalności.

#### <a name="recommended-action"></a>Zalecane działanie

Przekonwertuj wszelkie implementacje `IConnectionAdapter`, aby użyć nowego wzorca pośredniczącego, jak pokazano [poniżej](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
