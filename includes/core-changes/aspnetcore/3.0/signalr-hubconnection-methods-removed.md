---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394470"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="1616e-101">Sygnalizujący: HubConnection ResetSendPing i ResetTimeout metod</span><span class="sxs-lookup"><span data-stu-id="1616e-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="1616e-102">Metody `ResetSendPing` i `ResetTimeout` zostały usunięte z interfejsu API `HubConnection` sygnalizującego.</span><span class="sxs-lookup"><span data-stu-id="1616e-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="1616e-103">Metody te były pierwotnie przeznaczone wyłącznie do użytku wewnętrznego, ale zostały udostępnione w ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="1616e-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="1616e-104">Te metody nie będą dostępne od momentu wydania w ASP.NET Core 3,0 wersja zapoznawcza 4.</span><span class="sxs-lookup"><span data-stu-id="1616e-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="1616e-105">W przypadku dyskusji zobacz [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="1616e-105">For discussion, see [aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1616e-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1616e-106">Version introduced</span></span>

<span data-ttu-id="1616e-107">3.0</span><span class="sxs-lookup"><span data-stu-id="1616e-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1616e-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="1616e-108">Old behavior</span></span>

<span data-ttu-id="1616e-109">Dostępne interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="1616e-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1616e-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="1616e-110">New behavior</span></span>

<span data-ttu-id="1616e-111">Interfejsy API są usuwane.</span><span class="sxs-lookup"><span data-stu-id="1616e-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1616e-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="1616e-112">Reason for change</span></span>

<span data-ttu-id="1616e-113">Metody te były pierwotnie przeznaczone wyłącznie do użytku wewnętrznego, ale zostały udostępnione w ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="1616e-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1616e-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="1616e-114">Recommended action</span></span>

<span data-ttu-id="1616e-115">Nie używaj tych metod.</span><span class="sxs-lookup"><span data-stu-id="1616e-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="1616e-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1616e-116">Category</span></span>

<span data-ttu-id="1616e-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1616e-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1616e-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1616e-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
