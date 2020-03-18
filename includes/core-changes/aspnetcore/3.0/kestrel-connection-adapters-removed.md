---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902038"
---
### <a name="kestrel-connection-adapters-removed"></a>Pusstrel: Usunięto adaptery połączeń

W ramach ruchu, aby przenieść "pubternal" API `public` `IConnectionAdapter` do , pojęcie został usunięty z Kestrel. Karty połączeń są zastępowane za pomocą pośredników połączeń (podobnych do pośredników HTTP w potoku ASP.NET Core, ale dla połączeń niższego poziomu). Protokół HTTPS i rejestrowanie połączeń zostały przeniesione z kart połączeń do pośredniczenia połączenia. Te metody rozszerzenia powinny nadal działać bezproblemowo, ale szczegóły implementacji uległy zmianie.

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412). Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Elementy rozszerzalności kestrel zostały utworzone `IConnectionAdapter`przy użyciu .

#### <a name="new-behavior"></a>Nowe zachowanie

Elementy rozszerzalności kestrel są tworzone jako [pośredniczyć](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana ma na celu zapewnienie bardziej elastycznej architektury rozszerzalności.

#### <a name="recommended-action"></a>Zalecana akcja

Konwertuj `IConnectionAdapter` implementacje, aby użyć nowego wzorca pośrednieniu, jak pokazano [tutaj](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
