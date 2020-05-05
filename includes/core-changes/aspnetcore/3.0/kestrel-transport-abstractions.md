---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394122"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="6493d-101">Kestrel: skróty transportowe zostały usunięte i utworzone publicznie</span><span class="sxs-lookup"><span data-stu-id="6493d-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="6493d-102">W ramach przenoszenia z interfejsów API "pubternal" interfejsy API warstwy transportu Kestrel są udostępniane jako interfejs publiczny w `Microsoft.AspNetCore.Connections.Abstractions` bibliotece.</span><span class="sxs-lookup"><span data-stu-id="6493d-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6493d-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6493d-103">Version introduced</span></span>

<span data-ttu-id="6493d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="6493d-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6493d-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="6493d-105">Old behavior</span></span>

- <span data-ttu-id="6493d-106">Abstrakcje związane z transportem były dostępne `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="6493d-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="6493d-107">`ListenOptions.NoDelay` Właściwość była dostępna.</span><span class="sxs-lookup"><span data-stu-id="6493d-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6493d-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="6493d-108">New behavior</span></span>

- <span data-ttu-id="6493d-109">`IConnectionListener` Interfejs został wprowadzony w bibliotece, `Microsoft.AspNetCore.Connections.Abstractions` aby udostępnić najbardziej używane funkcje z `...Transport.Abstractions` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6493d-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="6493d-110">`NoDelay` Jest teraz dostępna w opcjach transportu (`LibuvTransportOptions` i `SocketTransportOptions`).</span><span class="sxs-lookup"><span data-stu-id="6493d-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="6493d-111">`SchedulingMode`nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="6493d-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6493d-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="6493d-112">Reason for change</span></span>

<span data-ttu-id="6493d-113">ASP.NET Core 3,0 został przeniesiony poza interfejsy API "pubternal".</span><span class="sxs-lookup"><span data-stu-id="6493d-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6493d-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6493d-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="6493d-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6493d-115">Category</span></span>

<span data-ttu-id="6493d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6493d-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6493d-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6493d-117">Affected APIs</span></span>

<span data-ttu-id="6493d-118">Brak</span><span class="sxs-lookup"><span data-stu-id="6493d-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
