---
ms.openlocfilehash: fa0f54404d1e14afa6ce48a425c984a48498a1ee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394094"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Sygnalizujący: HandshakeProtocol. SuccessHandshakeData został zastąpiony

Pole [HandshakeProtocol. SuccessHandshakeData](https://github.com/aspnet/AspNetCore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) zostało usunięte i zastąpione metodą pomocnika, która generuje pomyślną odpowiedź uzgadniania z określonym `IHubProtocol`. 

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`HandshakeProtocol.SuccessHandshakeData` było polem `public static ReadOnlyMemory<byte>`.

#### <a name="new-behavior"></a>Nowe zachowanie

`HandshakeProtocol.SuccessHandshakeData` został zastąpiony metodą `static` `GetSuccessfulHandshake(IHubProtocol protocol)`, która zwraca `ReadOnlyMemory<byte>` w oparciu o określony protokół. 

#### <a name="reason-for-change"></a>Przyczyna zmiany

Dodatkowe pola zostały dodane do _odpowiedzi_ uzgadniania, które nie są stałe i zmieniają się w zależności od wybranego protokołu.

#### <a name="recommended-action"></a>Zalecana akcja

Brak. Ten typ nie jest przeznaczony do użycia z kodu użytkownika. Jest ona `public`, więc może być współużytkowana przez serwer sygnalizujący i klienta. Mogą być również używane przez klientów sygnalizujących klientów pisanych w programie .NET. Ta zmiana nie powinna mieć żadnego wpływ na **użytkowników** sygnalizującego.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
