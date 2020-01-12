---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902038"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="7375d-101">Kestrel: Usunięto karty połączeń</span><span class="sxs-lookup"><span data-stu-id="7375d-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="7375d-102">W ramach przenoszenia, aby przenieść interfejsy API "pubternal" do `public`, koncepcja `IConnectionAdapter` została usunięta z Kestrel.</span><span class="sxs-lookup"><span data-stu-id="7375d-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="7375d-103">Karty połączeń są zastępowane przez oprogramowanie pośredniczące połączenia (podobne do oprogramowania pośredniczącego HTTP w potoku ASP.NET Core, ale w przypadku połączeń niższego poziomu).</span><span class="sxs-lookup"><span data-stu-id="7375d-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="7375d-104">Rejestrowanie protokołu HTTPS i połączeń zostało przeniesione z kart połączeń do oprogramowania pośredniczącego połączenia.</span><span class="sxs-lookup"><span data-stu-id="7375d-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="7375d-105">Te metody rozszerzające powinny nadal bezproblemowo współpracować, ale szczegóły implementacji zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="7375d-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="7375d-106">Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="7375d-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="7375d-107">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="7375d-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7375d-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7375d-108">Version introduced</span></span>

<span data-ttu-id="7375d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="7375d-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7375d-110">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="7375d-110">Old behavior</span></span>

<span data-ttu-id="7375d-111">Składniki rozszerzalności Kestrel zostały utworzone przy użyciu `IConnectionAdapter`.</span><span class="sxs-lookup"><span data-stu-id="7375d-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7375d-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="7375d-112">New behavior</span></span>

<span data-ttu-id="7375d-113">Składniki rozszerzalności Kestrel są tworzone jako [oprogramowanie pośredniczące](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="7375d-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7375d-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="7375d-114">Reason for change</span></span>

<span data-ttu-id="7375d-115">Ta zmiana ma na celu zapewnienie bardziej elastycznej architektury rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="7375d-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7375d-116">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="7375d-116">Recommended action</span></span>

<span data-ttu-id="7375d-117">Przekonwertuj wszelkie implementacje `IConnectionAdapter`, aby użyć nowego wzorca pośredniczącego, jak pokazano [poniżej](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="7375d-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="7375d-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7375d-118">Category</span></span>

<span data-ttu-id="7375d-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7375d-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7375d-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7375d-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
