---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901987"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="033ac-101">Buforowanie: Usunięto Właściwość CompactOnMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="033ac-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="033ac-102">W wersji ASP.NET Core 3,0 usunięto [przestarzałe interfejsy API MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="033ac-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="033ac-103">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="033ac-103">Change description</span></span>

<span data-ttu-id="033ac-104">Ta zmiana to kontynuacja dla elementu [ASPNET/buforowanie # 221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="033ac-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="033ac-105">Aby zapoznać się z omówieniem, zobacz [dotnet/Extensions # 1062](https://github.com/dotnet/extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="033ac-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="033ac-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="033ac-106">Version introduced</span></span>

<span data-ttu-id="033ac-107">3.0</span><span class="sxs-lookup"><span data-stu-id="033ac-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="033ac-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="033ac-108">Old behavior</span></span>

<span data-ttu-id="033ac-109">Właściwość `MemoryCacheOptions.CompactOnMemoryPressure` była dostępna.</span><span class="sxs-lookup"><span data-stu-id="033ac-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="033ac-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="033ac-110">New behavior</span></span>

<span data-ttu-id="033ac-111">Właściwość `MemoryCacheOptions.CompactOnMemoryPressure` została usunięta.</span><span class="sxs-lookup"><span data-stu-id="033ac-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="033ac-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="033ac-112">Reason for change</span></span>

<span data-ttu-id="033ac-113">Automatyczne kompaktowanie pamięci podręcznej powodowało problemy.</span><span class="sxs-lookup"><span data-stu-id="033ac-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="033ac-114">Aby uniknąć nieoczekiwanego zachowania, pamięć podręczna powinna być kompaktowana tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="033ac-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="033ac-115">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="033ac-115">Recommended action</span></span>

<span data-ttu-id="033ac-116">Aby skompaktować pamięć podręczną, downcast do `MemoryCache` i Wywołaj `Compact` w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="033ac-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="033ac-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="033ac-117">Category</span></span>

<span data-ttu-id="033ac-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="033ac-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="033ac-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="033ac-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
