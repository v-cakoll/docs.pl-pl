---
title: ICorDebugProcess5::EnumerateHeap — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: c8cfc9cdf6580a002f6ac15080012a9e8c63be20
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129646"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="1b45f-102">ICorDebugProcess5::EnumerateHeap — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b45f-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="1b45f-103">Pobiera moduł wyliczający dla obiektów na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="1b45f-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b45f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b45f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b45f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b45f-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="1b45f-106">określoną Wskaźnik do adresu obiektu interfejsu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) , który jest modułem wyliczającym dla obiektów, które znajdują się na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="1b45f-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b45f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b45f-107">Remarks</span></span>  
 <span data-ttu-id="1b45f-108">Przed wywołaniem metody `ICorDebugProcess5::EnumerateHeap` należy wywołać metodę [ICorDebugProcess5:: GetGCHeapInformation —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) i sprawdzić wartość pola `areGCStructuresValid` zwróconego obiektu [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) , aby upewnić się, że sterta wyrzucania elementów bezużytecznych w jej bieżący stan jest wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="1b45f-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="1b45f-109">Ponadto `ICorDebugProcess5::EnumerateHeap` zwraca `E_FAIL`, jeśli dołączysz zbyt wcześnie w okresie istnienia procesu, przed przydzieleniem pamięci dla zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="1b45f-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="1b45f-110">Obiekt interfejsu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu ICorDebugEnum, który umożliwia Wyliczenie obiektów [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="1b45f-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="1b45f-111">Ta metoda wypełnia obiekt kolekcji [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) z wystąpieniami [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które zawierają informacje o wszystkich obiektach.</span><span class="sxs-lookup"><span data-stu-id="1b45f-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="1b45f-112">Kolekcja może zawierać również wystąpienia [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które dostarczają informacji o obiektach, które nie zostały odblokowane przez żaden obiekt, ale jeszcze nie zostały zebrane przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1b45f-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b45f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b45f-113">Requirements</span></span>  
 <span data-ttu-id="1b45f-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b45f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b45f-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1b45f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b45f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1b45f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b45f-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b45f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b45f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b45f-118">See also</span></span>

- [<span data-ttu-id="1b45f-119">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b45f-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="1b45f-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1b45f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
