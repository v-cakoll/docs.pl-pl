---
title: ICorDebugVariableHomeEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: a9b65449747fde42f9cd770e33741ef34d33fbb8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121026"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="d8ec1-102">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8ec1-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="d8ec1-103">Dostarcza moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8ec1-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8ec1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d8ec1-104">Methods</span></span>  
  
|<span data-ttu-id="d8ec1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d8ec1-105">Method</span></span>|<span data-ttu-id="d8ec1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d8ec1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8ec1-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="d8ec1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="d8ec1-108">Pobiera określoną liczbę wystąpień [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) , które zawierają informacje o zmiennych lokalnych i argumentach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8ec1-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8ec1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8ec1-109">Remarks</span></span>  
 <span data-ttu-id="d8ec1-110">Interfejs `ICorDebugVariableHomeEnum` implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="d8ec1-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="d8ec1-111">Wystąpienie `ICorDebugVariableHomeEnum` jest wypełniane wystąpieniami [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) przez wywołanie metody [ICorDebugCode4:: EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d8ec1-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="d8ec1-112">Każde wystąpienie [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) w kolekcji reprezentuje zmienną lokalną lub argument w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8ec1-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="d8ec1-113">Obiekty [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugVariableHomeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d8ec1-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ec1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8ec1-114">Requirements</span></span>  
 <span data-ttu-id="d8ec1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ec1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ec1-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d8ec1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ec1-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d8ec1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ec1-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ec1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ec1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8ec1-119">See also</span></span>

- [<span data-ttu-id="d8ec1-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8ec1-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="d8ec1-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d8ec1-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
