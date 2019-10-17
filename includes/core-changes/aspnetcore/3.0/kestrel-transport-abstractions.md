---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394122"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: skróty transportowe zostały usunięte i utworzone publicznie

W ramach przenoszenia z interfejsów API "pubternal" interfejsy API warstwy transportu Kestrel są udostępniane jako interfejs publiczny w bibliotece `Microsoft.AspNetCore.Connections.Abstractions`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

- Abstrakcje związane z transportem były dostępne w bibliotece `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions`.
- Właściwość `ListenOptions.NoDelay` była dostępna.

#### <a name="new-behavior"></a>Nowe zachowanie

- Interfejs `IConnectionListener` został wprowadzony w bibliotece `Microsoft.AspNetCore.Connections.Abstractions`, aby uwidocznić najbardziej używane funkcje z biblioteki `...Transport.Abstractions`.
- @No__t-0 jest teraz dostępna w opcjach transportu (`LibuvTransportOptions` i `SocketTransportOptions`).
- `SchedulingMode` nie jest już dostępna.

#### <a name="reason-for-change"></a>Przyczyna zmiany

ASP.NET Core 3,0 został przeniesiony poza interfejsy API "pubternal".

#### <a name="recommended-action"></a>Zalecana akcja

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

### Affected APIs

Not detectable via API analysis

-->
