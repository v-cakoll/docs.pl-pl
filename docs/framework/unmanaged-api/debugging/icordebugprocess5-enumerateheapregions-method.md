---
title: ICorDebugProcess5::EnumerateHeapRegions — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61e30cf4ffe45578f7ad37de8295d227dbf313c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103964"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="094e0-102">ICorDebugProcess5::EnumerateHeapRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="094e0-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="094e0-103">Pobiera moduł wyliczający dla zakresów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="094e0-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="094e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="094e0-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="094e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="094e0-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="094e0-106">[out] Wskaźnik na adres [icordebugheapsegmentenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiektu interfejsu, który jest moduł wyliczający dla zakresów pamięci, w którym znajdują się obiekty w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="094e0-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="094e0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="094e0-107">Remarks</span></span>  
 <span data-ttu-id="094e0-108">Przed wywołaniem `ICorDebugProcess5::EnumerateHeapRegions` metody powinny wywoływać [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody i sprawdzić wartość `areGCStructuresValid` pole zwracanego [cor_heapinfo —](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) obiekt do upewnij się, że stercie wyrzucania elementów bezużytecznych w jego bieżącym stanie wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="094e0-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="094e0-109">Ponadto `ICorDebugProcess5::EnumerateHeapRegions` metoda zwraca `E_FAIL` po dołączeniu zbyt początkowym etapie istnienia procesu przed pamięci regiony są tworzone.</span><span class="sxs-lookup"><span data-stu-id="094e0-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="094e0-110">Ta metoda jest gwarantowane, wyliczyć wszystkie obszary pamięci, które mogą zawierać zarządzanych obiektów, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach.</span><span class="sxs-lookup"><span data-stu-id="094e0-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="094e0-111">[Icordebugheapsegmentenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiekt kolekcji mogą obejmować regiony pamięci puste lub zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="094e0-111">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="094e0-112">[Icordebugheapsegmentenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiektu interfejsu jest standardowy moduł wyliczający, pochodzące z icordebugenum — interfejs umożliwiający wyliczenie [cor_segment —](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="094e0-112">The [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) objects.</span></span> <span data-ttu-id="094e0-113">Każdy [cor_segment —](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) obiektu zawiera informacje o zakresie pamięci określonego segmentu, wraz z generacji obiektów w tym segmencie.</span><span class="sxs-lookup"><span data-stu-id="094e0-113">Each [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="094e0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="094e0-114">Requirements</span></span>  
 <span data-ttu-id="094e0-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="094e0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="094e0-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="094e0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="094e0-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="094e0-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="094e0-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="094e0-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="094e0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="094e0-119">See also</span></span>

- [<span data-ttu-id="094e0-120">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="094e0-120">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="094e0-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="094e0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
