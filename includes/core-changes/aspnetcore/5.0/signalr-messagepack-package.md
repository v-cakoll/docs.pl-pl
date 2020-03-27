---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345214"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a>SignalR: MessagePack Hub Protocol przeniesiony do pakietu MessagePack 2.x

Protokół ASP.NET Core SignalR [MessagePack Hub](/aspnet/core/signalr/messagepackhubprotocol) używa [pakietu MessagePack NuGet](https://www.nuget.org/packages/MessagePack) dla serializacji MessagePack. ASP.NET Core 5.0 uaktualnia pakiet z wersji 1.x do najnowszej wersji pakietu 2.x.

Aby do dyskusji na ten temat, zobacz [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).

#### <a name="version-introduced"></a>Wprowadzono wersję

5.0 Wersja zapoznawcza 1

#### <a name="old-behavior"></a>Stare zachowanie

ASP.NET Core SignalR używane MessagePack 1.x pakiet do serializacji i deserializacji messagepack wiadomości.

#### <a name="new-behavior"></a>Nowe zachowanie

ASP.NET Core SignalR używa messagepack 2.x pakiet do serializacji i deserializacji messagepack wiadomości.

#### <a name="reason-for-change"></a>Powód zmiany

Najnowsze ulepszenia w pakiecie MessagePack 2.x dodają przydatne funkcje.

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana podziału ma zastosowanie, gdy:

* Ustawianie lub konfigurowanie wartości na <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.
* Korzystanie z interfejsów API MessagePack bezpośrednio i przy użyciu ASP.NET Core SignalR MessagePack Hub Protocol w tym samym projekcie. Nowsza wersja zostanie załadowana zamiast poprzedniej wersji.

Aby uzyskać wskazówki dotyczące migracji od autorów pakietu, zobacz [Migrowanie z messagepack v1.x do messagepack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md). Niektóre aspekty serializacji wiadomości i deserializacji są zagrożone. W szczególności istnieją [zmiany behawioralne w sposobie serializacji wartości DateTime.](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
