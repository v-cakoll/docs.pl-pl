---
title: Interfejs ICorDebugVariableHomeEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum
helpviewer_keywords: ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7e64a52ca70606f83138b636f7ccb62ba18908f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="c7007-102">Interfejs ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="c7007-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="c7007-103">Udostępnia moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="c7007-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7007-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c7007-104">Methods</span></span>  
  
|<span data-ttu-id="c7007-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c7007-105">Method</span></span>|<span data-ttu-id="c7007-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c7007-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7007-107">Next — metoda</span><span class="sxs-lookup"><span data-stu-id="c7007-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="c7007-108">Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje o zmiennych lokalnych i argumenty w funkcji.</span><span class="sxs-lookup"><span data-stu-id="c7007-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7007-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7007-109">Remarks</span></span>  
 <span data-ttu-id="c7007-110">`ICorDebugVariableHomeEnum` Interfejsu implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="c7007-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="c7007-111">`ICorDebugVariableHomeEnum` Wystąpień jest wypełniana [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień przez wywołanie metody [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c7007-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="c7007-112">Każdy [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) reprezentuje wystąpienie w kolekcji lokalnej zmiennej lub argumentu dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="c7007-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="c7007-113">[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) mogą być wyliczane obiektów w kolekcji, wywołując [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c7007-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7007-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7007-114">Requirements</span></span>  
 <span data-ttu-id="c7007-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7007-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7007-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7007-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7007-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7007-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7007-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7007-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7007-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7007-119">See Also</span></span>  
 [<span data-ttu-id="c7007-120">Interfejs ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="c7007-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="c7007-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="c7007-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
