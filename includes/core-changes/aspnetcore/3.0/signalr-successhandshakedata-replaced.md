---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901618"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a>SignalR: HandshakeProtocol.SuccessHandshakeData zastąpiony

[Pole HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) zostało usunięte i zastąpione metodą pomocnika, która generuje pomyślną `IHubProtocol`odpowiedź uścisku dłoni, biorąc pod uwagę określoną .

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`HandshakeProtocol.SuccessHandshakeData`było `public static ReadOnlyMemory<byte>` polem.

#### <a name="new-behavior"></a>Nowe zachowanie

`HandshakeProtocol.SuccessHandshakeData`został zastąpiony metodą, `static` `GetSuccessfulHandshake(IHubProtocol protocol)` która `ReadOnlyMemory<byte>` zwraca na podstawie określonego protokołu.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Dodatkowe pola zostały dodane do _odpowiedzi_ uzgadniania, które nie są stałe i zmieniają się w zależności od wybranego protokołu.

#### <a name="recommended-action"></a>Zalecana akcja

Brak. Ten typ nie jest przeznaczony do użycia z kodu użytkownika. Jest `public`, dzięki czemu może być współużytkowany między serwerem SignalR i klientem. Może być również używany przez klientów SignalR klienta napisane w .NET. **Ta** zmiana nie powinna mieć wpływu na użytkowników SignalR.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
