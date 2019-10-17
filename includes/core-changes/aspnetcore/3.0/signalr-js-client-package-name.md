---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394443"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Sygnalizacja: zmieniono nazwę pakietu klienta języka JavaScript

W ASP.NET Core 3,0 w wersji zapoznawczej 7 nazwa pakietu klienta skryptu JavaScript została zmieniona z `@aspnet/signalr` na `@microsoft/signalr`. Zmiana nazwy odzwierciedla fakt, że sygnalizujący jest przydatny w więcej niż zaledwie ASP.NET Core aplikacji, dzięki usłudze Azure Signal Service.

Aby reagować na tę zmianę, Zmień odwołania w plikach *Package. JSON* , instrukcje `require` i instrukcje języka ECMAScript `import`. W ramach tej zmiany nazwy nie zostanie zmieniony żaden interfejs API.

W przypadku dyskusji zobacz [ASPNET/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet klienta miał nazwę `@aspnet/signalr`.

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
