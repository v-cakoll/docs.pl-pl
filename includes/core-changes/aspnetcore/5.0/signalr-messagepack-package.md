---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345214"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="b0b83-101">SignalR: MessagePack Hub Protocol przeniesiony do pakietu MessagePack 2.x</span><span class="sxs-lookup"><span data-stu-id="b0b83-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="b0b83-102">Protokół ASP.NET Core SignalR [MessagePack Hub](/aspnet/core/signalr/messagepackhubprotocol) używa [pakietu MessagePack NuGet](https://www.nuget.org/packages/MessagePack) dla serializacji MessagePack.</span><span class="sxs-lookup"><span data-stu-id="b0b83-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="b0b83-103">ASP.NET Core 5.0 uaktualnia pakiet z wersji 1.x do najnowszej wersji pakietu 2.x.</span><span class="sxs-lookup"><span data-stu-id="b0b83-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="b0b83-104">Aby do dyskusji na ten temat, zobacz [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span><span class="sxs-lookup"><span data-stu-id="b0b83-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b0b83-105">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="b0b83-105">Version introduced</span></span>

<span data-ttu-id="b0b83-106">5.0 Wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="b0b83-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b0b83-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="b0b83-107">Old behavior</span></span>

<span data-ttu-id="b0b83-108">ASP.NET Core SignalR używane MessagePack 1.x pakiet do serializacji i deserializacji messagepack wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0b83-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b0b83-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="b0b83-109">New behavior</span></span>

<span data-ttu-id="b0b83-110">ASP.NET Core SignalR używa messagepack 2.x pakiet do serializacji i deserializacji messagepack wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0b83-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b0b83-111">Powód zmiany</span><span class="sxs-lookup"><span data-stu-id="b0b83-111">Reason for change</span></span>

<span data-ttu-id="b0b83-112">Najnowsze ulepszenia w pakiecie MessagePack 2.x dodają przydatne funkcje.</span><span class="sxs-lookup"><span data-stu-id="b0b83-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b0b83-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b0b83-113">Recommended action</span></span>

<span data-ttu-id="b0b83-114">Ta zmiana podziału ma zastosowanie, gdy:</span><span class="sxs-lookup"><span data-stu-id="b0b83-114">This breaking change applies when:</span></span>

* <span data-ttu-id="b0b83-115">Ustawianie lub konfigurowanie wartości na <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span><span class="sxs-lookup"><span data-stu-id="b0b83-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="b0b83-116">Korzystanie z interfejsów API MessagePack bezpośrednio i przy użyciu ASP.NET Core SignalR MessagePack Hub Protocol w tym samym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b0b83-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="b0b83-117">Nowsza wersja zostanie załadowana zamiast poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="b0b83-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="b0b83-118">Aby uzyskać wskazówki dotyczące migracji od autorów pakietu, zobacz [Migrowanie z messagepack v1.x do messagepack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span><span class="sxs-lookup"><span data-stu-id="b0b83-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="b0b83-119">Niektóre aspekty serializacji wiadomości i deserializacji są zagrożone.</span><span class="sxs-lookup"><span data-stu-id="b0b83-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="b0b83-120">W szczególności istnieją [zmiany behawioralne w sposobie serializacji wartości DateTime.](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)</span><span class="sxs-lookup"><span data-stu-id="b0b83-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="b0b83-121">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b0b83-121">Category</span></span>

<span data-ttu-id="b0b83-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b0b83-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b0b83-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b0b83-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
