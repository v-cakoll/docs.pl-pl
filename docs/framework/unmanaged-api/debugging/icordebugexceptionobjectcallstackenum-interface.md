---
title: ICorDebugExceptionObjectCallStackEnum — Interfejs
ms.date: 03/30/2017
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
ms.openlocfilehash: 9d98bccdfb83cec547b185693c28f25017d3225f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782800"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="080cf-102">ICorDebugExceptionObjectCallStackEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="080cf-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="080cf-103">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="080cf-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="080cf-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="080cf-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="080cf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="080cf-105">Methods</span></span>  
  
|<span data-ttu-id="080cf-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="080cf-106">Method</span></span>|<span data-ttu-id="080cf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="080cf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="080cf-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="080cf-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="080cf-109">Pobiera określoną liczbę obiektów [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) , które zawierają informacje o stosie wywołań obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="080cf-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="080cf-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="080cf-110">Remarks</span></span>  
 <span data-ttu-id="080cf-111">Interfejs `ICorDebugExceptionObjectCallStackEnum` implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="080cf-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="080cf-112">Wystąpienie `ICorDebugExceptionObjectCallStackEnum` jest wypełniane obiektami [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) przez wywołanie metody [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack —](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="080cf-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="080cf-113">Elementy stosu wywołań w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="080cf-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="080cf-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="080cf-114">Requirements</span></span>  
 <span data-ttu-id="080cf-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="080cf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="080cf-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="080cf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="080cf-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="080cf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="080cf-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="080cf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="080cf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="080cf-119">See also</span></span>

- [<span data-ttu-id="080cf-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="080cf-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="080cf-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="080cf-121">Debugging</span></span>](index.md)
