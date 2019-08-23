---
title: ICorDebugCode4, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ec40de7fe9e12315987e65e48f1727f5d5b80ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960728"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="6479d-102">ICorDebugCode4, interfejs</span><span class="sxs-lookup"><span data-stu-id="6479d-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="6479d-103">Zapewnia metodę, która umożliwia debugerowi Wyliczenie zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="6479d-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6479d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6479d-104">Methods</span></span>  
  
|<span data-ttu-id="6479d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6479d-105">Method</span></span>|<span data-ttu-id="6479d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6479d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6479d-107">EnumerateVariableHomes, metoda</span><span class="sxs-lookup"><span data-stu-id="6479d-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="6479d-108">Pobiera moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.</span><span class="sxs-lookup"><span data-stu-id="6479d-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6479d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6479d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6479d-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6479d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6479d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6479d-111">Requirements</span></span>  
 <span data-ttu-id="6479d-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6479d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6479d-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6479d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6479d-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6479d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6479d-115">**.NET Framework wersje:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6479d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6479d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6479d-116">See also</span></span>

- [<span data-ttu-id="6479d-117">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6479d-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="6479d-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6479d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
