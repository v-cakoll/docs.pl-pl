---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394122"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="b2608-101">Kestrel: skróty transportowe zostały usunięte i utworzone publicznie</span><span class="sxs-lookup"><span data-stu-id="b2608-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="b2608-102">W ramach przenoszenia z interfejsów API "pubternal" interfejsy API warstwy transportu Kestrel są udostępniane jako interfejs publiczny w bibliotece `Microsoft.AspNetCore.Connections.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="b2608-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b2608-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="b2608-103">Version introduced</span></span>

<span data-ttu-id="b2608-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b2608-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b2608-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="b2608-105">Old behavior</span></span>

- <span data-ttu-id="b2608-106">Abstrakcje związane z transportem były dostępne w bibliotece `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="b2608-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="b2608-107">Właściwość `ListenOptions.NoDelay` była dostępna.</span><span class="sxs-lookup"><span data-stu-id="b2608-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b2608-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="b2608-108">New behavior</span></span>

- <span data-ttu-id="b2608-109">Interfejs `IConnectionListener` został wprowadzony w bibliotece `Microsoft.AspNetCore.Connections.Abstractions`, aby uwidocznić najbardziej używane funkcje z biblioteki `...Transport.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="b2608-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="b2608-110">@No__t-0 jest teraz dostępna w opcjach transportu (`LibuvTransportOptions` i `SocketTransportOptions`).</span><span class="sxs-lookup"><span data-stu-id="b2608-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="b2608-111">`SchedulingMode` nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="b2608-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b2608-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="b2608-112">Reason for change</span></span>

<span data-ttu-id="b2608-113">ASP.NET Core 3,0 został przeniesiony poza interfejsy API "pubternal".</span><span class="sxs-lookup"><span data-stu-id="b2608-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b2608-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b2608-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="b2608-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b2608-115">Category</span></span>

<span data-ttu-id="b2608-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2608-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b2608-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b2608-117">Affected APIs</span></span>

<span data-ttu-id="b2608-118">Brak</span><span class="sxs-lookup"><span data-stu-id="b2608-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
