---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394269"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="70411-101">Buforowanie: Usunięto Właściwość CompactOnMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="70411-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="70411-102">W wersji ASP.NET Core 3,0 usunięto [przestarzałe interfejsy API MemoryCacheOptions](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="70411-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="70411-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="70411-103">Change description</span></span>

<span data-ttu-id="70411-104">Ta zmiana to kontynuacja dla elementu [ASPNET/buforowanie # 221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="70411-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="70411-105">W przypadku dyskusji zobacz [ASPNET/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="70411-105">For discussion, see [aspnet/Extensions#1062](https://github.com/aspnet/Extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="70411-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="70411-106">Version introduced</span></span>

<span data-ttu-id="70411-107">3.0</span><span class="sxs-lookup"><span data-stu-id="70411-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="70411-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="70411-108">Old behavior</span></span>

<span data-ttu-id="70411-109">Właściwość `MemoryCacheOptions.CompactOnMemoryPressure` była dostępna.</span><span class="sxs-lookup"><span data-stu-id="70411-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="70411-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="70411-110">New behavior</span></span>

<span data-ttu-id="70411-111">Właściwość `MemoryCacheOptions.CompactOnMemoryPressure` została usunięta.</span><span class="sxs-lookup"><span data-stu-id="70411-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="70411-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="70411-112">Reason for change</span></span>

<span data-ttu-id="70411-113">Automatyczne kompaktowanie pamięci podręcznej powodowało problemy.</span><span class="sxs-lookup"><span data-stu-id="70411-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="70411-114">Aby uniknąć nieoczekiwanego zachowania, pamięć podręczna powinna być kompaktowana tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="70411-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="70411-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="70411-115">Recommended action</span></span>

<span data-ttu-id="70411-116">Aby skompaktować pamięć podręczną, downcast do `MemoryCache` i Wywołaj `Compact` w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="70411-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="70411-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="70411-117">Category</span></span>

<span data-ttu-id="70411-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="70411-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="70411-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="70411-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
