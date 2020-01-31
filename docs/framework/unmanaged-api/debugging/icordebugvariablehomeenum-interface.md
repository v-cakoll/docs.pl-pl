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
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790949"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="bc9c8-102">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc9c8-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="bc9c8-103">Dostarcza moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc9c8-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc9c8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bc9c8-104">Methods</span></span>  
  
|<span data-ttu-id="bc9c8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bc9c8-105">Method</span></span>|<span data-ttu-id="bc9c8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bc9c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc9c8-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="bc9c8-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="bc9c8-108">Pobiera określoną liczbę wystąpień [ICorDebugVariableHome](icordebugvariablehome-interface.md) , które zawierają informacje o zmiennych lokalnych i argumentach w funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc9c8-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc9c8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc9c8-109">Remarks</span></span>  
 <span data-ttu-id="bc9c8-110">Interfejs `ICorDebugVariableHomeEnum` implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="bc9c8-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="bc9c8-111">Wystąpienie `ICorDebugVariableHomeEnum` jest wypełniane wystąpieniami [ICorDebugVariableHome](icordebugvariablehome-interface.md) przez wywołanie metody [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bc9c8-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="bc9c8-112">Każde wystąpienie [ICorDebugVariableHome](icordebugvariablehome-interface.md) w kolekcji reprezentuje zmienną lokalną lub argument w funkcji.</span><span class="sxs-lookup"><span data-stu-id="bc9c8-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="bc9c8-113">Obiekty [ICorDebugVariableHome](icordebugvariablehome-interface.md) w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bc9c8-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc9c8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc9c8-114">Requirements</span></span>  
 <span data-ttu-id="bc9c8-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc9c8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc9c8-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bc9c8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc9c8-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bc9c8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc9c8-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc9c8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc9c8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc9c8-119">See also</span></span>

- [<span data-ttu-id="bc9c8-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc9c8-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="bc9c8-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc9c8-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
