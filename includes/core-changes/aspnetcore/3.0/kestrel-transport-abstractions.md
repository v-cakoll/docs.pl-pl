---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721776"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: skróty transportowe zostały usunięte i utworzone publicznie

W ramach przenoszenia z interfejsów API "pubternal" interfejsy API warstwy transportu Kestrel są udostępniane jako interfejs publiczny w `Microsoft.AspNetCore.Connections.Abstractions` bibliotece.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

- Abstrakcje związane z transportem były dostępne w `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` bibliotece.
- `ListenOptions.NoDelay`Właściwość była dostępna.

#### <a name="new-behavior"></a>Nowe zachowanie

- `IConnectionListener`Interfejs został wprowadzony w bibliotece, `Microsoft.AspNetCore.Connections.Abstractions` Aby udostępnić najbardziej używane funkcje z `...Transport.Abstractions` biblioteki.
- `NoDelay`Jest teraz dostępna w opcjach transportu ( `LibuvTransportOptions` i `SocketTransportOptions` ).
- `SchedulingMode`nie jest już dostępny.

#### <a name="reason-for-change"></a>Przyczyna zmiany

ASP.NET Core 3,0 został przeniesiony poza interfejsy API "pubternal".

#### <a name="recommended-action"></a>Zalecana akcja

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
