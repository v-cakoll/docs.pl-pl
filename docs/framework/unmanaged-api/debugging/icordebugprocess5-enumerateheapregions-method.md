---
title: "ICorDebugProcess5::EnumerateHeapRegions — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeapRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1365ed5fd8cf308716b16d78e79a26584bd966c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="478f2-102">ICorDebugProcess5::EnumerateHeapRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="478f2-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="478f2-103">Pobiera moduł wyliczający dla zakresów pamięci sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="478f2-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="478f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="478f2-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="478f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="478f2-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="478f2-106">[out] Wskaźnik do adresu [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiektu interfejsu, który moduł wyliczający dla zakresów pamięci, w którym obiekty znajdują się w stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="478f2-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="478f2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="478f2-107">Remarks</span></span>  
 <span data-ttu-id="478f2-108">Przed wywołaniem `ICorDebugProcess5::EnumerateHeapRegions` metody powinny wywoływać [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) — metoda i sprawdź, czy wartość `areGCStructuresValid` pole zwracana [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) obiekt w celu zapewnienia wyliczalny pamięci sterty kolekcji w jego bieżącym stanie.</span><span class="sxs-lookup"><span data-stu-id="478f2-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="478f2-109">Ponadto `ICorDebugProcess5::EnumerateHeapRegions` metoda zwraca `E_FAIL` po dołączeniu zbyt wcześnie w okresie istnienia procesu przed pamięci regiony są tworzone.</span><span class="sxs-lookup"><span data-stu-id="478f2-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="478f2-110">Ta metoda jest gwarantowana wyliczyć wszystkie regiony pamięci, które mogą zawierać obiektów zarządzanych, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w regionach.</span><span class="sxs-lookup"><span data-stu-id="478f2-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="478f2-111">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiektu kolekcji może zawierać regiony pamięci pusty lub zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="478f2-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="478f2-112">[ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiekt interfejsu jest standardowy moduł pochodną ICorDebugEnum — interfejs umożliwiający wyliczenie [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="478f2-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="478f2-113">Każdy [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) obiektu zawiera informacje o pamięci z zakresu określonego segmentu, oraz generowanie obiektów w tym segmencie.</span><span class="sxs-lookup"><span data-stu-id="478f2-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="478f2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="478f2-114">Requirements</span></span>  
 <span data-ttu-id="478f2-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="478f2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="478f2-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="478f2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="478f2-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="478f2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="478f2-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="478f2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="478f2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="478f2-119">See Also</span></span>  
 [<span data-ttu-id="478f2-120">ICorDebugProcess5 — interfejs</span><span class="sxs-lookup"><span data-stu-id="478f2-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="478f2-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="478f2-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
