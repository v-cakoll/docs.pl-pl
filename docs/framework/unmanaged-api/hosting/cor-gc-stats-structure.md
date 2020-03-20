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
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176529"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="175e9-102">COR_GC_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="175e9-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="175e9-103">Zawiera statystyki dotyczące mechanizmu wyrzucania elementów bezużytecznych środowiska wykonawczego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="175e9-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="175e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="175e9-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="175e9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="175e9-105">Members</span></span>  
  
|<span data-ttu-id="175e9-106">Członek</span><span class="sxs-lookup"><span data-stu-id="175e9-106">Member</span></span>|<span data-ttu-id="175e9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="175e9-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="175e9-108">Wskazuje, które wartości pól powinny być obliczane i zwracane.</span><span class="sxs-lookup"><span data-stu-id="175e9-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="175e9-109">Wskazuje liczbę wyrzucanych elementów bezużytecznych, które zostały wymuszone przez żądanie zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="175e9-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="175e9-110">Wskazuje liczbę wyrzucanych elementów bezużytecznych wykonanych dla każdej generacji.</span><span class="sxs-lookup"><span data-stu-id="175e9-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="175e9-111">Całkowita liczba kilobajtów popełnionych we wszystkich stertach.</span><span class="sxs-lookup"><span data-stu-id="175e9-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="175e9-112">Całkowita liczba kilobajtów zarezerwowanych na wszystkich stertach.</span><span class="sxs-lookup"><span data-stu-id="175e9-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="175e9-113">Rozmiar w kilobajtach sterty zerowej generacji.</span><span class="sxs-lookup"><span data-stu-id="175e9-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="175e9-114">Rozmiar w kilobajtach sterty generacji.</span><span class="sxs-lookup"><span data-stu-id="175e9-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="175e9-115">Rozmiar w kilobajtach sterty generacji two.</span><span class="sxs-lookup"><span data-stu-id="175e9-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="175e9-116">Rozmiar ( kilobajtów) sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="175e9-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="175e9-117">Rozmiar w kilobajtach obiektów promowanych od generacji od zera do generacji.</span><span class="sxs-lookup"><span data-stu-id="175e9-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="175e9-118">Rozmiar w kilobajtach obiektów promowanych od pierwszej do drugiej generacji.</span><span class="sxs-lookup"><span data-stu-id="175e9-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="175e9-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="175e9-119">Remarks</span></span>  
 <span data-ttu-id="175e9-120">[ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) Metoda wymaga `Flags` pola `COR_GC_STATS` struktury, które mają być ustawione na jedną lub więcej wartości [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wyliczenia, aby określić, które statystyki mają być ustawione.</span><span class="sxs-lookup"><span data-stu-id="175e9-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="175e9-121">W poniższej tabeli przedstawiono statystyki dostarczone przez tę strukturę na `COR_GC_COUNTS` dwie `COR_GC_MEMORYUSAGE` [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wartości wyliczenia i .</span><span class="sxs-lookup"><span data-stu-id="175e9-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="175e9-122">Określony przez COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="175e9-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="175e9-123">Określony przez COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="175e9-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="175e9-124">Przykład użycia jest następujący:</span><span class="sxs-lookup"><span data-stu-id="175e9-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="175e9-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="175e9-125">Requirements</span></span>  
 <span data-ttu-id="175e9-126">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="175e9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="175e9-127">**Nagłówek:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="175e9-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="175e9-128">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="175e9-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="175e9-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="175e9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="175e9-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="175e9-130">See also</span></span>

- [<span data-ttu-id="175e9-131">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="175e9-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="175e9-132">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="175e9-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="175e9-133">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="175e9-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
