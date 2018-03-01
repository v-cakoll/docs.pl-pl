---
title: "ICorDebugExceptionObjectCallStackEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f353ecaf4f0a64920fa7e23b98d09ef3191428cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="184a0-102">ICorDebugExceptionObjectCallStackEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="184a0-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="184a0-103">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="184a0-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="184a0-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="184a0-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="184a0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="184a0-105">Methods</span></span>  
  
|<span data-ttu-id="184a0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="184a0-106">Method</span></span>|<span data-ttu-id="184a0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="184a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="184a0-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="184a0-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="184a0-109">Pobiera określoną liczbę [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektów, które zawierają informacje dotyczące stosu wywołań obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="184a0-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="184a0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="184a0-110">Remarks</span></span>  
 <span data-ttu-id="184a0-111">`ICorDebugExceptionObjectCallStackEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="184a0-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="184a0-112">`ICorDebugExceptionObjectCallStackEnum` Wystąpień jest wypełniana [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektów przez wywołanie metody [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="184a0-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="184a0-113">Mogą być wyliczane elementy stosu wywołań w kolekcji, wywołując [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) — metoda</span><span class="sxs-lookup"><span data-stu-id="184a0-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="184a0-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="184a0-114">Requirements</span></span>  
 <span data-ttu-id="184a0-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="184a0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="184a0-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="184a0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="184a0-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="184a0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="184a0-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="184a0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184a0-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="184a0-119">See Also</span></span>  
 [<span data-ttu-id="184a0-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="184a0-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="184a0-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="184a0-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
