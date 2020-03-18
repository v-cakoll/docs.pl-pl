---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901746"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: Zmieniono nazwę pakietu klienta JavaScript

W ASP.NET Core 3.0 Preview 7 nazwa pakietu klienta `@aspnet/signalr` `@microsoft/signalr`SignalR JavaScript została zmieniona z . Zmiana nazwy odzwierciedla fakt, że SignalR jest przydatne w więcej niż tylko ASP.NET podstawowych aplikacji, dzięki usłudze Azure SignalR Service.

Aby zareagować na tę zmianę, zmień odwołania `require` w plikach `import` *package.json,* instrukcjach i instrukcjach ECMAScript. Żaden interfejs API nie zmieni się w ramach tej zmiany nazwy.

Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet klienta został `@aspnet/signalr`nazwany .

#### <a name="new-behavior"></a>Nowe zachowanie

Pakiet klienta nosi `@microsoft/signalr`nazwę .

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiana nazwy wyjaśnia, że SignalR jest przydatne poza ASP.NET aplikacje Core, dzięki usłudze Azure SignalR Service.

#### <a name="recommended-action"></a>Zalecana akcja

Przełącz się `@microsoft/signalr`do nowego pakietu .

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
