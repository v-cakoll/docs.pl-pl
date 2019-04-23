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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e67e4685320f56a4a6a8be2e3eb2e6c8065ce59
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080387"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="a185e-102">ICorDebugVariableHomeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a185e-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="a185e-103">Dostarcza moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="a185e-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a185e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a185e-104">Methods</span></span>  
  
|<span data-ttu-id="a185e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a185e-105">Method</span></span>|<span data-ttu-id="a185e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a185e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a185e-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="a185e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="a185e-108">Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje dotyczące zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="a185e-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a185e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a185e-109">Remarks</span></span>  
 <span data-ttu-id="a185e-110">`ICorDebugVariableHomeEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="a185e-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a185e-111">`ICorDebugVariableHomeEnum` Wystąpień jest wypełniana przy użyciu [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, wywołując [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a185e-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="a185e-112">Każdy [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) reprezentuje wystąpienie w kolekcji, zmienna lokalna lub argumentu dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="a185e-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="a185e-113">[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a185e-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a185e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a185e-114">Requirements</span></span>  
 <span data-ttu-id="a185e-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a185e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a185e-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a185e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a185e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a185e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a185e-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a185e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a185e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a185e-119">See also</span></span>

- [<span data-ttu-id="a185e-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="a185e-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="a185e-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a185e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
