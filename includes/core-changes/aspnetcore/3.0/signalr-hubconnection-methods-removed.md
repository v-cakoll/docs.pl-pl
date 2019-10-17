---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394470"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a>Sygnalizujący: HubConnection ResetSendPing i ResetTimeout metod

Metody `ResetSendPing` i `ResetTimeout` zostały usunięte z interfejsu API `HubConnection` sygnalizującego. Metody te były pierwotnie przeznaczone wyłącznie do użytku wewnętrznego, ale zostały udostępnione w ASP.NET Core 2,2. Te metody nie będą dostępne od momentu wydania w ASP.NET Core 3,0 wersja zapoznawcza 4. W przypadku dyskusji zobacz [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Dostępne interfejsy API.

#### <a name="new-behavior"></a>Nowe zachowanie

Interfejsy API są usuwane.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Metody te były pierwotnie przeznaczone wyłącznie do użytku wewnętrznego, ale zostały udostępnione w ASP.NET Core 2,2.

#### <a name="recommended-action"></a>Zalecana akcja

Nie używaj tych metod.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
