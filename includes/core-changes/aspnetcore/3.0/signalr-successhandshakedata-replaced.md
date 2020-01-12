---
ms.openlocfilehash: 1d8bcaf68d44f27642048c1c207b52c55b604690
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901618"
---
### <a name="signalr-handshakeprotocolsuccesshandshakedata-replaced"></a><span data-ttu-id="3063f-101">Sygnalizujący: HandshakeProtocol. SuccessHandshakeData został zastąpiony</span><span class="sxs-lookup"><span data-stu-id="3063f-101">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>

<span data-ttu-id="3063f-102">Pole [HandshakeProtocol. SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) zostało usunięte i zastąpione metodą pomocnika, która generuje pomyślną odpowiedź uzgadniania z określonym `IHubProtocol`.</span><span class="sxs-lookup"><span data-stu-id="3063f-102">The [HandshakeProtocol.SuccessHandshakeData](https://github.com/dotnet/aspnetcore/blob/c5b2bc0df2a0027832bf7d01dfb19ca39cd08ae6/src/SignalR/common/SignalR.Common/src/Protocol/HandshakeProtocol.cs#L27) field was removed and replaced with a helper method that generates a successful handshake response given a specific `IHubProtocol`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3063f-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3063f-103">Version introduced</span></span>

<span data-ttu-id="3063f-104">3.0</span><span class="sxs-lookup"><span data-stu-id="3063f-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3063f-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="3063f-105">Old behavior</span></span>

<span data-ttu-id="3063f-106">`HandshakeProtocol.SuccessHandshakeData` było `public static ReadOnlyMemory<byte>` polem.</span><span class="sxs-lookup"><span data-stu-id="3063f-106">`HandshakeProtocol.SuccessHandshakeData` was a `public static ReadOnlyMemory<byte>` field.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3063f-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="3063f-107">New behavior</span></span>

<span data-ttu-id="3063f-108">`HandshakeProtocol.SuccessHandshakeData` został zastąpiony przez metodę `static` `GetSuccessfulHandshake(IHubProtocol protocol)`, która zwraca `ReadOnlyMemory<byte>` w oparciu o określony protokół.</span><span class="sxs-lookup"><span data-stu-id="3063f-108">`HandshakeProtocol.SuccessHandshakeData` has been replaced by a `static` `GetSuccessfulHandshake(IHubProtocol protocol)` method that returns a `ReadOnlyMemory<byte>` based on the specified protocol.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3063f-109">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="3063f-109">Reason for change</span></span>

<span data-ttu-id="3063f-110">Dodatkowe pola zostały dodane do _odpowiedzi_ uzgadniania, które nie są stałe i zmieniają się w zależności od wybranego protokołu.</span><span class="sxs-lookup"><span data-stu-id="3063f-110">Additional fields were added to the handshake _response_ that are non-constant and change depending on the selected protocol.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3063f-111">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="3063f-111">Recommended action</span></span>

<span data-ttu-id="3063f-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="3063f-112">None.</span></span> <span data-ttu-id="3063f-113">Ten typ nie jest przeznaczony do użycia z kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3063f-113">This type isn't designed for use from user code.</span></span> <span data-ttu-id="3063f-114">Jest ona `public`, więc może być współużytkowana przez serwer sygnalizujący i klienta.</span><span class="sxs-lookup"><span data-stu-id="3063f-114">It's `public`, so it can be shared between the SignalR server and client.</span></span> <span data-ttu-id="3063f-115">Mogą być również używane przez klientów sygnalizujących klientów pisanych w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="3063f-115">It may also be used by customer SignalR clients written in .NET.</span></span> <span data-ttu-id="3063f-116">Ta zmiana nie powinna mieć żadnego wpływ na **użytkowników** sygnalizującego.</span><span class="sxs-lookup"><span data-stu-id="3063f-116">**Users** of SignalR shouldn't be affected by this change.</span></span>

#### <a name="category"></a><span data-ttu-id="3063f-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3063f-117">Category</span></span>

<span data-ttu-id="3063f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3063f-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3063f-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3063f-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData?displayProperty=namewithType>

<!--

#### Affected APIs

`F:Microsoft.AspNetCore.SignalR.Protocol.HandshakeProtocol.SuccessHandshakeData`

-->
