---
title: "ICorDebugProcess5::EnumerateHeap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41cd7d47650cdfe6a3598ba126be489107181a44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="99778-102">ICorDebugProcess5::EnumerateHeap — Metoda</span><span class="sxs-lookup"><span data-stu-id="99778-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="99778-103">Pobiera moduł wyliczający dla obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="99778-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99778-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99778-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99778-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99778-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="99778-106">[out] Wskaźnik do adresu [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu interfejsu, który moduł wyliczający dla obiektów, które znajdują się na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="99778-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99778-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99778-107">Remarks</span></span>  
 <span data-ttu-id="99778-108">Przed wywołaniem `ICorDebugProcess5::EnumerateHeap` metody powinny wywoływać [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) — metoda i sprawdź, czy wartość `areGCStructuresValid` pole zwracana [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) obiekt w celu zapewnienia wyliczalny pamięci sterty kolekcji w jego bieżącym stanie.</span><span class="sxs-lookup"><span data-stu-id="99778-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="99778-109">Ponadto `ICorDebugProcess5::EnumerateHeap` zwraca `E_FAIL` Jeśli dołączeniu zbyt wcześnie w okresie istnienia procesu przed pamięci dla sterty zarządzanej został przydzielony.</span><span class="sxs-lookup"><span data-stu-id="99778-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="99778-110">[ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiekt interfejsu jest standardowy moduł pochodną ICorDebugEnum — interfejs umożliwiający wyliczenie [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="99778-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="99778-111">Ta metoda umożliwia wypełnienie [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) obiektu kolekcji z [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje o wszystkich obiektów.</span><span class="sxs-lookup"><span data-stu-id="99778-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="99778-112">Kolekcja może również obejmować [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obiektów, które nie są osadzone przez żaden obiekt, ale nie zostały zgromadzone przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="99778-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99778-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99778-113">Requirements</span></span>  
 <span data-ttu-id="99778-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99778-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99778-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99778-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99778-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99778-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99778-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99778-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99778-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99778-118">See Also</span></span>  
 [<span data-ttu-id="99778-119">ICorDebugProcess5 — interfejs</span><span class="sxs-lookup"><span data-stu-id="99778-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="99778-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="99778-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
