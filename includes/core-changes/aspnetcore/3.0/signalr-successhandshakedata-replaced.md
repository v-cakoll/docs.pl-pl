---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901618"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>Sygnalizujący: HandshakeProtocol. SuccessHandshakeData został zastąpiony

Pole [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) zostało usunięte i zastąpione metodą pomocnika, która generuje pomyślną odpowiedź uzgadniania z określonym `IHubProtocol`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`HandshakeProtocol.SuccessHandshakeData` było `public static ReadOnlyMemory<byte>` polem.

#### <a name="new-behavior"></a>Nowe zachowanie

`HandshakeProtocol.SuccessHandshakeData` został zastąpiony przez metodę `static` `GetSuccessfulHandshake(IHubProtocol protocol)`, która zwraca `ReadOnlyMemory<byte>` w oparciu o określony protokół.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Dodatkowe pola zostały dodane do _odpowiedzi_ uzgadniania, które nie są stałe i zmieniają się w zależności od wybranego protokołu.

#### <a name="recommended-action"></a>Zalecane działanie

Brak. Ten typ nie jest przeznaczony do użycia z kodu użytkownika. Jest ona `public`, więc może być współużytkowana przez serwer sygnalizujący i klienta. Mogą być również używane przez klientów sygnalizujących klientów pisanych w programie .NET. Ta zmiana nie powinna mieć żadnego wpływ na **użytkowników** sygnalizującego.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
