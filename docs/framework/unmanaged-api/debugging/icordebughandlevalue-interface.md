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
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794457"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="df984-102">ICorDebugHandleValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="df984-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="df984-103">Podklasa elementu ICorDebugReferenceValue, która reprezentuje wartość odniesienia, do której debuger utworzył dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="df984-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df984-104">Metody</span><span class="sxs-lookup"><span data-stu-id="df984-104">Methods</span></span>  
  
|<span data-ttu-id="df984-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="df984-105">Method</span></span>|<span data-ttu-id="df984-106">Opis</span><span class="sxs-lookup"><span data-stu-id="df984-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df984-107">Dispose, metoda</span><span class="sxs-lookup"><span data-stu-id="df984-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="df984-108">Zwalnia dojście, do którego odwołuje się ten obiekt `ICorDebugHandleValue` bez jawnego zwalniania wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="df984-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="df984-109">GetHandleType, metoda</span><span class="sxs-lookup"><span data-stu-id="df984-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="df984-110">Pobiera wartość CorDebugHandleType —, która opisuje rodzaj dojścia, do którego odwołuje się ten `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="df984-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df984-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df984-111">Remarks</span></span>  
 <span data-ttu-id="df984-112">Obiekt `ICorDebugReferenceValue` jest unieważniony przez przerwanie w trakcie wykonywania debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="df984-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="df984-113">`ICorDebugHandleValue` utrzymuje odwołanie poprzez przerwy i kontynuacje, dopóki nie zostanie jawnie wydane.</span><span class="sxs-lookup"><span data-stu-id="df984-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df984-114">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="df984-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df984-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df984-115">Requirements</span></span>  
 <span data-ttu-id="df984-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df984-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df984-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df984-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df984-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df984-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df984-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df984-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df984-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df984-120">See also</span></span>

- [<span data-ttu-id="df984-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="df984-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
