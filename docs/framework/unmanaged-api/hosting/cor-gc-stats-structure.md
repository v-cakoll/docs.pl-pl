---
title: "COR_GC_STATS — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STATS
helpviewer_keywords: COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7c620c4a33032711abc0d7b82af908018bd44cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corgcstats-structure"></a><span data-ttu-id="82650-102">COR_GC_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="82650-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="82650-103">Udostępnia statystykę mechanizmu kolekcji garbage środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="82650-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82650-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82650-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="82650-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="82650-105">Members</span></span>  
  
|<span data-ttu-id="82650-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="82650-106">Member</span></span>|<span data-ttu-id="82650-107">Opis</span><span class="sxs-lookup"><span data-stu-id="82650-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="82650-108">Określa wartości pola, które powinny być obliczany i zwracany.</span><span class="sxs-lookup"><span data-stu-id="82650-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="82650-109">Wskazuje liczbę operacji wyrzucania, które zostały wymuszone przez żądania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="82650-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="82650-110">Wskazuje liczbę operacji wyrzucania wykonywane dla każdego generacji.</span><span class="sxs-lookup"><span data-stu-id="82650-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="82650-111">Całkowita liczba zatwierdzone we wszystkich stertach kilobajtów.</span><span class="sxs-lookup"><span data-stu-id="82650-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="82650-112">Całkowita liczba zarezerwowanych we wszystkich stertach kilobajtów.</span><span class="sxs-lookup"><span data-stu-id="82650-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="82650-113">Rozmiar w kilobajtach sterty generowania od zera.</span><span class="sxs-lookup"><span data-stu-id="82650-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="82650-114">Rozmiar w kilobajtach sterty generowania-do-jednego.</span><span class="sxs-lookup"><span data-stu-id="82650-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="82650-115">Rozmiar w kilobajtach sterty pokolenia 2.</span><span class="sxs-lookup"><span data-stu-id="82650-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="82650-116">Rozmiar w kilobajtach sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="82650-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="82650-117">Rozmiar w kilobajtach obiektów awansowane z pokolenia 0 na pokolenie jeden.</span><span class="sxs-lookup"><span data-stu-id="82650-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="82650-118">Rozmiar w kilobajtach awansowana z Generowanie jednego generacji dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="82650-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82650-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82650-119">Remarks</span></span>  
 <span data-ttu-id="82650-120">[ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda wymaga `Flags` pole `COR_GC_STATS` struktury, należy ustawić jedną lub więcej wartości [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wyliczeniu, aby określić, które statystyki mają być tworzone.</span><span class="sxs-lookup"><span data-stu-id="82650-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="82650-121">Poniższa tabela mapuje dostarczonych przez tę strukturę do dwóch statystyk [cor_gc_stat_types —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) wartości wyliczenia `COR_GC_COUNTS` i `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="82650-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="82650-122">Określony przez COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="82650-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="82650-123">Określony przez COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="82650-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="82650-124">Przykład użycia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="82650-124">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="82650-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82650-125">Requirements</span></span>  
 <span data-ttu-id="82650-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82650-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82650-127">**Nagłówek:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="82650-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="82650-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82650-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82650-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82650-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82650-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82650-130">See Also</span></span>  
 [<span data-ttu-id="82650-131">Hosting — struktury</span><span class="sxs-lookup"><span data-stu-id="82650-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="82650-132">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="82650-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="82650-133">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="82650-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
