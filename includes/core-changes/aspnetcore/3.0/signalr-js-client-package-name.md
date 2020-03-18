---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901746"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="98588-101">SignalR: Zmieniono nazwę pakietu klienta JavaScript</span><span class="sxs-lookup"><span data-stu-id="98588-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="98588-102">W ASP.NET Core 3.0 Preview 7 nazwa pakietu klienta `@aspnet/signalr` `@microsoft/signalr`SignalR JavaScript została zmieniona z .</span><span class="sxs-lookup"><span data-stu-id="98588-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="98588-103">Zmiana nazwy odzwierciedla fakt, że SignalR jest przydatne w więcej niż tylko ASP.NET podstawowych aplikacji, dzięki usłudze Azure SignalR Service.</span><span class="sxs-lookup"><span data-stu-id="98588-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="98588-104">Aby zareagować na tę zmianę, zmień odwołania `require` w plikach `import` *package.json,* instrukcjach i instrukcjach ECMAScript.</span><span class="sxs-lookup"><span data-stu-id="98588-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="98588-105">Żaden interfejs API nie zmieni się w ramach tej zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="98588-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="98588-106">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="98588-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98588-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="98588-107">Version introduced</span></span>

<span data-ttu-id="98588-108">3.0</span><span class="sxs-lookup"><span data-stu-id="98588-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="98588-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="98588-109">Old behavior</span></span>

<span data-ttu-id="98588-110">Pakiet klienta został `@aspnet/signalr`nazwany .</span><span class="sxs-lookup"><span data-stu-id="98588-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="98588-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="98588-111">New behavior</span></span>

<span data-ttu-id="98588-112">Pakiet klienta nosi `@microsoft/signalr`nazwę .</span><span class="sxs-lookup"><span data-stu-id="98588-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="98588-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="98588-113">Reason for change</span></span>

<span data-ttu-id="98588-114">Zmiana nazwy wyjaśnia, że SignalR jest przydatne poza ASP.NET aplikacje Core, dzięki usłudze Azure SignalR Service.</span><span class="sxs-lookup"><span data-stu-id="98588-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98588-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="98588-115">Recommended action</span></span>

<span data-ttu-id="98588-116">Przełącz się `@microsoft/signalr`do nowego pakietu .</span><span class="sxs-lookup"><span data-stu-id="98588-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="98588-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="98588-117">Category</span></span>

<span data-ttu-id="98588-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="98588-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98588-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="98588-119">Affected APIs</span></span>

<span data-ttu-id="98588-120">Brak</span><span class="sxs-lookup"><span data-stu-id="98588-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
