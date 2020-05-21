---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721776"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="66b1a-101">Kestrel: skróty transportowe zostały usunięte i utworzone publicznie</span><span class="sxs-lookup"><span data-stu-id="66b1a-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="66b1a-102">W ramach przenoszenia z interfejsów API "pubternal" interfejsy API warstwy transportu Kestrel są udostępniane jako interfejs publiczny w `Microsoft.AspNetCore.Connections.Abstractions` bibliotece.</span><span class="sxs-lookup"><span data-stu-id="66b1a-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="66b1a-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="66b1a-103">Version introduced</span></span>

<span data-ttu-id="66b1a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="66b1a-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="66b1a-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="66b1a-105">Old behavior</span></span>

- <span data-ttu-id="66b1a-106">Abstrakcje związane z transportem były dostępne w `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` bibliotece.</span><span class="sxs-lookup"><span data-stu-id="66b1a-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="66b1a-107">`ListenOptions.NoDelay`Właściwość była dostępna.</span><span class="sxs-lookup"><span data-stu-id="66b1a-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="66b1a-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="66b1a-108">New behavior</span></span>

- <span data-ttu-id="66b1a-109">`IConnectionListener`Interfejs został wprowadzony w bibliotece, `Microsoft.AspNetCore.Connections.Abstractions` Aby udostępnić najbardziej używane funkcje z `...Transport.Abstractions` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="66b1a-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="66b1a-110">`NoDelay`Jest teraz dostępna w opcjach transportu ( `LibuvTransportOptions` i `SocketTransportOptions` ).</span><span class="sxs-lookup"><span data-stu-id="66b1a-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="66b1a-111">`SchedulingMode`nie jest już dostępny.</span><span class="sxs-lookup"><span data-stu-id="66b1a-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="66b1a-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="66b1a-112">Reason for change</span></span>

<span data-ttu-id="66b1a-113">ASP.NET Core 3,0 został przeniesiony poza interfejsy API "pubternal".</span><span class="sxs-lookup"><span data-stu-id="66b1a-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="66b1a-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="66b1a-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="66b1a-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="66b1a-115">Category</span></span>

<span data-ttu-id="66b1a-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="66b1a-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="66b1a-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="66b1a-117">Affected APIs</span></span>

<span data-ttu-id="66b1a-118">Brak</span><span class="sxs-lookup"><span data-stu-id="66b1a-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
