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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d335a62545f06a66d4044b59aa9499d3f7ede515
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208478"
---
# <a name="corgcstats-structure"></a><span data-ttu-id="19572-102">COR_GC_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="19572-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="19572-103">Przedstawia dane statystyczne dotyczące mechanizmu kolekcji wyrzucania elementów środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="19572-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19572-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19572-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="19572-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="19572-105">Members</span></span>  
  
|<span data-ttu-id="19572-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="19572-106">Member</span></span>|<span data-ttu-id="19572-107">Opis</span><span class="sxs-lookup"><span data-stu-id="19572-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="19572-108">Wskazuje wartości pola, które powinny być obliczany i zwracany.</span><span class="sxs-lookup"><span data-stu-id="19572-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="19572-109">Wskazuje liczbę wyrzucania elementów bezużytecznych, które zostały zmuszeni przez zewnętrzne żądanie.</span><span class="sxs-lookup"><span data-stu-id="19572-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="19572-110">Wskazuje liczbę wyrzucania elementów bezużytecznych wykonywane dla każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="19572-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="19572-111">Całkowita liczba kilobajtów zatwierdzone we wszystkich stertach.</span><span class="sxs-lookup"><span data-stu-id="19572-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="19572-112">Całkowita liczba kilobajtów zastrzeżone we wszystkich stertach.</span><span class="sxs-lookup"><span data-stu-id="19572-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="19572-113">Rozmiar w kilobajtach sterty generowania od zera.</span><span class="sxs-lookup"><span data-stu-id="19572-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="19572-114">Rozmiar w kilobajtach sterty jeden generacji.</span><span class="sxs-lookup"><span data-stu-id="19572-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="19572-115">Rozmiar w kilobajtach sterty pokolenia 2.</span><span class="sxs-lookup"><span data-stu-id="19572-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="19572-116">Rozmiar w kilobajtach stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="19572-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="19572-117">Rozmiar w kilobajtach obiektów promowane z generacji 0 do generowania jednego.</span><span class="sxs-lookup"><span data-stu-id="19572-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="19572-118">Rozmiar w kilobajtach obiektów promowane z generowania jeden generacji dwa.</span><span class="sxs-lookup"><span data-stu-id="19572-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19572-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19572-119">Remarks</span></span>  
 <span data-ttu-id="19572-120">[Iclrgcmanager::getstats —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda wymaga `Flags` pole `COR_GC_STATS` struktury, należy ustawić jedną lub więcej wartości [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wyliczeniu, aby określić, które statystyki mają być tworzone.</span><span class="sxs-lookup"><span data-stu-id="19572-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="19572-121">Poniższa tabela zawiera mapowanie dostarczonych przez tę strukturę do dwóch statystyk [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wartości wyliczenia `COR_GC_COUNTS` i `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="19572-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="19572-122">Określony przez COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="19572-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="19572-123">Określony przez COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="19572-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="19572-124">Przykład użycia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="19572-124">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="19572-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19572-125">Requirements</span></span>  
 <span data-ttu-id="19572-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19572-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19572-127">**Nagłówek:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="19572-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="19572-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19572-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="19572-129">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="19572-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19572-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19572-130">See also</span></span>

- [<span data-ttu-id="19572-131">Hosting — Struktury</span><span class="sxs-lookup"><span data-stu-id="19572-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="19572-132">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="19572-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="19572-133">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="19572-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
