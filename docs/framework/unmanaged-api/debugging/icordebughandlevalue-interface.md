---
title: ICorDebugHandleValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915005"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="6a229-102">ICorDebugHandleValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a229-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="6a229-103">Podklasa elementu ICorDebugReferenceValue, która reprezentuje wartość odniesienia, do której debuger utworzył dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6a229-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a229-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6a229-104">Methods</span></span>  
  
|<span data-ttu-id="6a229-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6a229-105">Method</span></span>|<span data-ttu-id="6a229-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6a229-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a229-107">Dispose, metoda</span><span class="sxs-lookup"><span data-stu-id="6a229-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="6a229-108">Zwalnia dojście, do którego `ICorDebugHandleValue` odwołuje się ten obiekt bez jawnego zwalniania wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6a229-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="6a229-109">GetHandleType, metoda</span><span class="sxs-lookup"><span data-stu-id="6a229-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="6a229-110">Pobiera wartość CorDebugHandleType —, która opisuje rodzaj dojścia, do którego odwołuje się ten `ICorDebugHandleValue`element.</span><span class="sxs-lookup"><span data-stu-id="6a229-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a229-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a229-111">Remarks</span></span>  
 <span data-ttu-id="6a229-112">`ICorDebugReferenceValue` Obiekt jest unieważniony przez przerwanie w trakcie wykonywania debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6a229-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="6a229-113">`ICorDebugHandleValue` Zachowuje swoje odwołanie poprzez przerwy i kontynuacje, dopóki nie zostanie jawnie wydane.</span><span class="sxs-lookup"><span data-stu-id="6a229-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a229-114">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6a229-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a229-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a229-115">Requirements</span></span>  
 <span data-ttu-id="6a229-116">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a229-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a229-117">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a229-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a229-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a229-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a229-119">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a229-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a229-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a229-120">See also</span></span>

- [<span data-ttu-id="6a229-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6a229-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
