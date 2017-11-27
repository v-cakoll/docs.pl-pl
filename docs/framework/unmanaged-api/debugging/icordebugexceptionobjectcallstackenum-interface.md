---
title: "ICorDebugExceptionObjectCallStackEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords: ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4814de2de71ba0fa4d1400f0be27fa4942febf54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="6e2a3-102">ICorDebugExceptionObjectCallStackEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6e2a3-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="6e2a3-103">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6e2a3-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="6e2a3-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="6e2a3-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e2a3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6e2a3-105">Methods</span></span>  
  
|<span data-ttu-id="6e2a3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6e2a3-106">Method</span></span>|<span data-ttu-id="6e2a3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6e2a3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e2a3-108">ICorDebugExceptionObjectCallStackEnum::Next</span><span class="sxs-lookup"><span data-stu-id="6e2a3-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="6e2a3-109">Pobiera określoną liczbę [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektów, które zawierają informacje dotyczące stosu wywołań obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6e2a3-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e2a3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e2a3-110">Remarks</span></span>  
 <span data-ttu-id="6e2a3-111">`ICorDebugExceptionObjectCallStackEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="6e2a3-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="6e2a3-112">`ICorDebugExceptionObjectCallStackEnum` Wystąpień jest wypełniana [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektów przez wywołanie metody [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6e2a3-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="6e2a3-113">Mogą być wyliczane elementy stosu wywołań w kolekcji, wywołując [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) — metoda</span><span class="sxs-lookup"><span data-stu-id="6e2a3-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e2a3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e2a3-114">Requirements</span></span>  
 <span data-ttu-id="6e2a3-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e2a3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e2a3-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e2a3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e2a3-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e2a3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e2a3-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e2a3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e2a3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e2a3-119">See Also</span></span>  
 [<span data-ttu-id="6e2a3-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="6e2a3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6e2a3-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6e2a3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
