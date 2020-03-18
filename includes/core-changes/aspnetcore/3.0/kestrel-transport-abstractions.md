---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394122"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a>Kestrel: Abstrakcje transportowe usunięte i upublicznione

W ramach odejścia od "pubternal" interfejsów API, interfejsy API warstwy transportu `Microsoft.AspNetCore.Connections.Abstractions` kestrel są udostępniane jako interfejs publiczny w bibliotece.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

- Abstrakcje związane z transportem `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` były dostępne w bibliotece.
- Obiekt `ListenOptions.NoDelay` był dostępny.

#### <a name="new-behavior"></a>Nowe zachowanie

- Interfejs `IConnectionListener` został wprowadzony `Microsoft.AspNetCore.Connections.Abstractions` w bibliotece, aby udostępnić `...Transport.Abstractions` najczęściej używane funkcje z biblioteki.
- Jest `NoDelay` teraz dostępna w`LibuvTransportOptions` opcjach transportu ( i `SocketTransportOptions`).
- `SchedulingMode`nie jest już dostępna.

#### <a name="reason-for-change"></a>Przyczyna zmiany

ASP.NET Core 3.0 odsunął się od interfejsów API "pubternal".

#### <a name="recommended-action"></a>Zalecana akcja

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

### Affected APIs

Not detectable via API analysis

-->
