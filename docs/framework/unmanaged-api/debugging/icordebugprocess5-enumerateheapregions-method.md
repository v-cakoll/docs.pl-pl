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
ms.openlocfilehash: 8070b0693b5718ad8b4cbeb9bf5792cb7f4a0a85
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792404"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="1dd96-102">ICorDebugProcess5::EnumerateHeapRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="1dd96-102">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>
<span data-ttu-id="1dd96-103">Pobiera moduł wyliczający dla zakresów pamięci zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="1dd96-103">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dd96-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dd96-105">Parameters</span></span>  
 `ppRegions`  
 <span data-ttu-id="1dd96-106">określoną Wskaźnik do adresu obiektu interfejsu [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) , który jest modułem wyliczającym dla zakresów pamięci, w których obiekty znajdują się w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="1dd96-106">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dd96-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1dd96-107">Remarks</span></span>  
 <span data-ttu-id="1dd96-108">Przed wywołaniem metody `ICorDebugProcess5::EnumerateHeapRegions` należy wywołać metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) i sprawdzić wartość pola `areGCStructuresValid` zwróconego obiektu [COR_HEAPINFO](cor-heapinfo-structure.md) , aby upewnić się, że sterta wyrzucania elementów bezużytecznych w bieżącym stanie jest wyliczalna.</span><span class="sxs-lookup"><span data-stu-id="1dd96-108">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="1dd96-109">Ponadto Metoda `ICorDebugProcess5::EnumerateHeapRegions` zwraca `E_FAIL`, jeśli dołączysz zbyt wcześnie w okresie istnienia procesu, przed utworzeniem regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="1dd96-109">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="1dd96-110">Ta metoda gwarantuje Wyliczenie wszystkich regionów pamięci, które mogą zawierać obiekty zarządzane, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w tych regionach.</span><span class="sxs-lookup"><span data-stu-id="1dd96-110">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="1dd96-111">Obiekt kolekcji [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) może zawierać puste lub zarezerwowane regiony pamięci.</span><span class="sxs-lookup"><span data-stu-id="1dd96-111">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="1dd96-112">Obiekt interfejsu [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu ICorDebugEnum, który umożliwia Wyliczenie [COR_SEGMENT](cor-segment-structure.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="1dd96-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="1dd96-113">Każdy obiekt [COR_SEGMENT](cor-segment-structure.md) zawiera informacje o zakresie pamięci określonego segmentu oraz o generowaniu obiektów w tym segmencie.</span><span class="sxs-lookup"><span data-stu-id="1dd96-113">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd96-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dd96-114">Requirements</span></span>  
 <span data-ttu-id="1dd96-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd96-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd96-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1dd96-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dd96-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1dd96-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dd96-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd96-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd96-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dd96-119">See also</span></span>

- [<span data-ttu-id="1dd96-120">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="1dd96-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="1dd96-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1dd96-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
