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
ms.openlocfilehash: 9386c77cc98df17d797d5886e1603ffc4824b6dc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205234"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="ea2a0-102">ICorDebugProcess5::EnumerateHeap — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea2a0-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="ea2a0-103">Pobiera moduł wyliczający dla obiektów na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea2a0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea2a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea2a0-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="ea2a0-106">określoną Wskaźnik do adresu obiektu interfejsu [ICorDebugHeapEnum](icordebugheapenum-interface.md) , który jest modułem wyliczającym dla obiektów, które znajdują się na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea2a0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea2a0-107">Remarks</span></span>  
 <span data-ttu-id="ea2a0-108">Przed wywołaniem `ICorDebugProcess5::EnumerateHeap` metody należy wywołać metodę [ICorDebugProcess5:: GetGCHeapInformation —](icordebugprocess5-getgcheapinformation-method.md) i sprawdzić wartość `areGCStructuresValid` pola zwróconego obiektu [COR_HEAPINFO](cor-heapinfo-structure.md) , aby upewnić się, że sterta wyrzucania elementów bezużytecznych w bieżącym stanie jest wyliczalna.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="ea2a0-109">Ponadto `ICorDebugProcess5::EnumerateHeap` zwraca wartość, `E_FAIL` Jeśli dołączysz zbyt wcześnie w okresie istnienia procesu, zanim zostanie przypisana pamięć zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="ea2a0-110">Obiekt interfejsu [ICorDebugHeapEnum](icordebugheapenum-interface.md) to standardowy moduł wyliczający pochodzący z interfejsu ICorDebugEnum, który umożliwia Wyliczenie [COR_HEAPOBJECT](cor-heapobject-structure.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="ea2a0-111">Ta metoda wypełnia obiekt kolekcji [ICorDebugHeapEnum](icordebugheapenum-interface.md) z wystąpieniami [COR_HEAPOBJECT](cor-heapobject-structure.md) , które zawierają informacje o wszystkich obiektach.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="ea2a0-112">Kolekcja może również zawierać [COR_HEAPOBJECT](cor-heapobject-structure.md) wystąpienia, które dostarczają informacji o obiektach, które nie są odblokowane przez żaden obiekt, ale nie zostały jeszcze zebrane przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ea2a0-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2a0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea2a0-113">Requirements</span></span>  
 <span data-ttu-id="ea2a0-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea2a0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2a0-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea2a0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea2a0-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ea2a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea2a0-117">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2a0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea2a0-118">See also</span></span>

- [<span data-ttu-id="ea2a0-119">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ea2a0-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="ea2a0-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ea2a0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
