---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394122"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: skróty transportowe zostały usunięte i utworzone publicznie

W ramach przenoszenia z interfejsów API "pubternal" interfejsy API warstwy transportu Kestrel są udostępniane jako interfejs publiczny w `Microsoft.AspNetCore.Connections.Abstractions` bibliotece.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

- Abstrakcje związane z transportem były dostępne `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` w bibliotece.
- `ListenOptions.NoDelay` Właściwość była dostępna.

#### <a name="new-behavior"></a>Nowe zachowanie

- `IConnectionListener` Interfejs został wprowadzony w bibliotece, `Microsoft.AspNetCore.Connections.Abstractions` aby udostępnić najbardziej używane funkcje z `...Transport.Abstractions` biblioteki.
- `NoDelay` Jest teraz dostępna w opcjach transportu (`LibuvTransportOptions` i `SocketTransportOptions`).
- `SchedulingMode`nie jest już dostępny.

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
