---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902038"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="87ccd-101">Kestrel: Usunięto karty połączeń</span><span class="sxs-lookup"><span data-stu-id="87ccd-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="87ccd-102">W ramach przeniesień do przenoszenia interfejsów API "pubternal" `public`do programu `IConnectionAdapter` powstała koncepcja została usunięta z Kestrel.</span><span class="sxs-lookup"><span data-stu-id="87ccd-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="87ccd-103">Karty połączeń są zastępowane przez oprogramowanie pośredniczące połączenia (podobne do oprogramowania pośredniczącego HTTP w potoku ASP.NET Core, ale w przypadku połączeń niższego poziomu).</span><span class="sxs-lookup"><span data-stu-id="87ccd-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="87ccd-104">Rejestrowanie protokołu HTTPS i połączeń zostało przeniesione z kart połączeń do oprogramowania pośredniczącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="87ccd-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="87ccd-105">Te metody rozszerzające powinny nadal bezproblemowo współpracować, ale szczegóły implementacji zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="87ccd-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="87ccd-106">Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="87ccd-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="87ccd-107">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="87ccd-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="87ccd-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="87ccd-108">Version introduced</span></span>

<span data-ttu-id="87ccd-109">3.0</span><span class="sxs-lookup"><span data-stu-id="87ccd-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="87ccd-110">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="87ccd-110">Old behavior</span></span>

<span data-ttu-id="87ccd-111">Składniki rozszerzalności Kestrel zostały utworzone `IConnectionAdapter`przy użyciu programu.</span><span class="sxs-lookup"><span data-stu-id="87ccd-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="87ccd-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="87ccd-112">New behavior</span></span>

<span data-ttu-id="87ccd-113">Składniki rozszerzalności Kestrel są tworzone jako [oprogramowanie pośredniczące](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="87ccd-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="87ccd-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="87ccd-114">Reason for change</span></span>

<span data-ttu-id="87ccd-115">Ta zmiana ma na celu zapewnienie bardziej elastycznej architektury rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="87ccd-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87ccd-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="87ccd-116">Recommended action</span></span>

<span data-ttu-id="87ccd-117">Konwertuj wszelkie implementacje `IConnectionAdapter` programu, aby użyć nowego wzorca pośredniczącego, jak pokazano [poniżej](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="87ccd-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="87ccd-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="87ccd-118">Category</span></span>

<span data-ttu-id="87ccd-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="87ccd-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87ccd-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="87ccd-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
