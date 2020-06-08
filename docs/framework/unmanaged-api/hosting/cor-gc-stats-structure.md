---
title: COR_GC_STATS — Struktura
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 7a6553de31d4f9627809af7691218c39dc734c6f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501667"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="da676-102">COR_GC_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="da676-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="da676-103">Zawiera dane statystyczne dotyczące mechanizmu odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="da676-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da676-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da676-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="da676-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="da676-105">Members</span></span>  
  
|<span data-ttu-id="da676-106">Członek</span><span class="sxs-lookup"><span data-stu-id="da676-106">Member</span></span>|<span data-ttu-id="da676-107">Opis</span><span class="sxs-lookup"><span data-stu-id="da676-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="da676-108">Wskazuje, które wartości pól należy obliczyć i zwrócić.</span><span class="sxs-lookup"><span data-stu-id="da676-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="da676-109">Wskazuje liczbę wyrzucania elementów bezużytecznych, które zostały wymuszone przez żądanie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="da676-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="da676-110">Wskazuje liczbę wyrzucania elementów bezużytecznych wykonanych dla każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="da676-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="da676-111">Łączna liczba kilobajtów zakontraktowanych we wszystkich stertach.</span><span class="sxs-lookup"><span data-stu-id="da676-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="da676-112">Łączna liczba kilobajtów zarezerwowanych na wszystkie sterty.</span><span class="sxs-lookup"><span data-stu-id="da676-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="da676-113">Rozmiar sterty generacji — w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="da676-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="da676-114">Rozmiar (w kilobajtach) sterty generacji.</span><span class="sxs-lookup"><span data-stu-id="da676-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="da676-115">Rozmiar (w kilobajtach) sterty generacji-2.</span><span class="sxs-lookup"><span data-stu-id="da676-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="da676-116">Rozmiar sterty dużego obiektu (w kilobajtach).</span><span class="sxs-lookup"><span data-stu-id="da676-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="da676-117">Rozmiar (w kilobajtach) obiektów, które zostały podwyższenie poziomu generacji zero w celu wygenerowania jednej.</span><span class="sxs-lookup"><span data-stu-id="da676-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="da676-118">Rozmiar (w kilobajtach) obiektów awansowanych od generacji jednej do generacji dwóch.</span><span class="sxs-lookup"><span data-stu-id="da676-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da676-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da676-119">Remarks</span></span>  
 <span data-ttu-id="da676-120">Metoda [ICLRGCManager::](iclrgcmanager-getstats-method.md) getstatistics wymaga, aby `Flags` pole `COR_GC_STATS` struktury było ustawione na co najmniej jedną wartość wyliczenia [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) , aby określić, które statystyki mają być ustawione.</span><span class="sxs-lookup"><span data-stu-id="da676-120">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="da676-121">Poniższa tabela zawiera mapy statystyk dostarczonych przez tę strukturę do dwóch [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) wartości wyliczenia `COR_GC_COUNTS` i `COR_GC_MEMORYUSAGE` .</span><span class="sxs-lookup"><span data-stu-id="da676-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="da676-122">Określone przez COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="da676-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="da676-123">Określone przez COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="da676-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="da676-124">Przykładem użycia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="da676-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="da676-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da676-125">Requirements</span></span>  
 <span data-ttu-id="da676-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da676-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da676-127">**Nagłówek:** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="da676-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="da676-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="da676-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da676-129">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da676-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da676-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da676-130">See also</span></span>

- [<span data-ttu-id="da676-131">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="da676-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="da676-132">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="da676-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="da676-133">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="da676-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
