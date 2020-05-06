---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901746"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Sygnalizacja: zmieniono nazwę pakietu klienta języka JavaScript

W programie ASP.NET Core 3,0 w wersji zapoznawczej 7 nazwa pakietu klienta języka JavaScript `@aspnet/signalr` została `@microsoft/signalr`zmieniona z na. Zmiana nazwy odzwierciedla fakt, że sygnalizujący jest przydatny w więcej niż zaledwie ASP.NET Core aplikacji, dzięki usłudze Azure Signal Service.

Aby reagować na tę zmianę, Zmień odwołania w plikach *Package. JSON* , `require` instrukcje i instrukcje języka ECMAScript `import` . W ramach tej zmiany nazwy nie zostanie zmieniony żaden interfejs API.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet klienta został nazwany `@aspnet/signalr`.

#### <a name="new-behavior"></a>Nowe zachowanie

Pakiet klienta ma nazwę `@microsoft/signalr`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiana nazwy objaśnia, że sygnalizujący jest przydatne poza ASP.NET Core aplikacjami, dzięki usłudze Azure Signal Service.

#### <a name="recommended-action"></a>Zalecana akcja

Przejdź do nowego pakietu `@microsoft/signalr`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
