---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901808"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="4547e-101">SignalR: Usunięto metody Resetowania i resetowania czasu usługi HubConnection ResetSendPing i Resettimeout</span><span class="sxs-lookup"><span data-stu-id="4547e-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="4547e-102">I `ResetSendPing` `ResetTimeout` metody zostały usunięte z `HubConnection` interfejsu API SignalR.</span><span class="sxs-lookup"><span data-stu-id="4547e-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="4547e-103">Metody te były pierwotnie przeznaczone wyłącznie do użytku wewnętrznego, ale zostały upublicznione w ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="4547e-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="4547e-104">Te metody nie będą dostępne począwszy od wersji ASP.NET Core 3.0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="4547e-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="4547e-105">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="4547e-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4547e-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4547e-106">Version introduced</span></span>

<span data-ttu-id="4547e-107">3.0</span><span class="sxs-lookup"><span data-stu-id="4547e-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4547e-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="4547e-108">Old behavior</span></span>

<span data-ttu-id="4547e-109">Interfejsy API były dostępne.</span><span class="sxs-lookup"><span data-stu-id="4547e-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4547e-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="4547e-110">New behavior</span></span>

<span data-ttu-id="4547e-111">Interfejsy API są usuwane.</span><span class="sxs-lookup"><span data-stu-id="4547e-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4547e-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="4547e-112">Reason for change</span></span>

<span data-ttu-id="4547e-113">Metody te były pierwotnie przeznaczone wyłącznie do użytku wewnętrznego, ale zostały upublicznione w ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="4547e-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4547e-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4547e-114">Recommended action</span></span>

<span data-ttu-id="4547e-115">Nie należy używać tych metod.</span><span class="sxs-lookup"><span data-stu-id="4547e-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="4547e-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4547e-116">Category</span></span>

<span data-ttu-id="4547e-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4547e-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4547e-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4547e-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->
