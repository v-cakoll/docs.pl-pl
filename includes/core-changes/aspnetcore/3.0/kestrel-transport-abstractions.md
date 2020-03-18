---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394122"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="eeea8-101">Kestrel: Abstrakcje transportowe usunięte i upublicznione</span><span class="sxs-lookup"><span data-stu-id="eeea8-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="eeea8-102">W ramach odejścia od "pubternal" interfejsów API, interfejsy API warstwy transportu `Microsoft.AspNetCore.Connections.Abstractions` kestrel są udostępniane jako interfejs publiczny w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="eeea8-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eeea8-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="eeea8-103">Version introduced</span></span>

<span data-ttu-id="eeea8-104">3.0</span><span class="sxs-lookup"><span data-stu-id="eeea8-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="eeea8-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="eeea8-105">Old behavior</span></span>

- <span data-ttu-id="eeea8-106">Abstrakcje związane z transportem `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` były dostępne w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="eeea8-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="eeea8-107">Obiekt `ListenOptions.NoDelay` był dostępny.</span><span class="sxs-lookup"><span data-stu-id="eeea8-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="eeea8-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="eeea8-108">New behavior</span></span>

- <span data-ttu-id="eeea8-109">Interfejs `IConnectionListener` został wprowadzony `Microsoft.AspNetCore.Connections.Abstractions` w bibliotece, aby udostępnić `...Transport.Abstractions` najczęściej używane funkcje z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="eeea8-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="eeea8-110">Jest `NoDelay` teraz dostępna w`LibuvTransportOptions` opcjach transportu ( i `SocketTransportOptions`).</span><span class="sxs-lookup"><span data-stu-id="eeea8-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="eeea8-111">`SchedulingMode`nie jest już dostępna.</span><span class="sxs-lookup"><span data-stu-id="eeea8-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eeea8-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="eeea8-112">Reason for change</span></span>

<span data-ttu-id="eeea8-113">ASP.NET Core 3.0 odsunął się od interfejsów API "pubternal".</span><span class="sxs-lookup"><span data-stu-id="eeea8-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eeea8-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="eeea8-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="eeea8-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="eeea8-115">Category</span></span>

<span data-ttu-id="eeea8-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eeea8-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eeea8-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="eeea8-117">Affected APIs</span></span>

<span data-ttu-id="eeea8-118">Brak</span><span class="sxs-lookup"><span data-stu-id="eeea8-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
