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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d080145ac63882e04412b44c34d040a75746243
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767528"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="30545-102">ICorDebugProcess5::EnumerateHeap — Metoda</span><span class="sxs-lookup"><span data-stu-id="30545-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="30545-103">Pobiera moduł wyliczający dla obiektów na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="30545-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30545-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30545-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30545-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30545-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="30545-106">[out] Wskaźnik na adres [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu, który jest moduł wyliczający dla obiektów, które znajdują się na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="30545-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30545-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30545-107">Remarks</span></span>  
 <span data-ttu-id="30545-108">Przed wywołaniem `ICorDebugProcess5::EnumerateHeap` metody powinny wywoływać [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody i sprawdzić wartość `areGCStructuresValid` pole zwracanego [cor_heapinfo —](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) obiekt do upewnij się, że stercie wyrzucania elementów bezużytecznych w jego bieżącym stanie wyliczalny.</span><span class="sxs-lookup"><span data-stu-id="30545-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="30545-109">Ponadto `ICorDebugProcess5::EnumerateHeap` zwraca `E_FAIL` Jeśli dołączysz zbyt wcześnie w trakcie trwania procesu przed pamięci dla zarządzanego stosu jest przydzielony.</span><span class="sxs-lookup"><span data-stu-id="30545-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="30545-110">[Icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu jest standardowy moduł wyliczający, pochodzące z icordebugenum — interfejs umożliwiający wyliczenie [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="30545-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="30545-111">Ta metoda wypełni [icordebugheapenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu kolekcji z [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które udostępniają informacje o wszystkich obiektach.</span><span class="sxs-lookup"><span data-stu-id="30545-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="30545-112">Kolekcja może również obejmować [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje o obiektach, które nie są zakorzenione przez żaden obiektu, ale nie został zebrany przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="30545-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30545-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30545-113">Requirements</span></span>  
 <span data-ttu-id="30545-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30545-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30545-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30545-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30545-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30545-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30545-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30545-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30545-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30545-118">See also</span></span>

- [<span data-ttu-id="30545-119">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="30545-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="30545-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="30545-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
