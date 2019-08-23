---
title: ICorDebugCode3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4efcf6d477ab006e179e283ca4ce7b62c27018a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960769"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="80609-102">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="80609-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="80609-103">Zapewnia metodę, która rozszerza wartości "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzanej zwracanej wartość.</span><span class="sxs-lookup"><span data-stu-id="80609-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80609-104">Metody</span><span class="sxs-lookup"><span data-stu-id="80609-104">Methods</span></span>  
  
|<span data-ttu-id="80609-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="80609-105">Method</span></span>|<span data-ttu-id="80609-106">Opis</span><span class="sxs-lookup"><span data-stu-id="80609-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80609-107">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="80609-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="80609-108">W przypadku określonego przesunięcia IL pobiera natywne przesunięcia, w których powinien być umieszczony punkt przerwania, aby debuger mógł uzyskać wartość zwracaną z funkcji.</span><span class="sxs-lookup"><span data-stu-id="80609-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80609-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80609-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80609-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="80609-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80609-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80609-111">Requirements</span></span>  
 <span data-ttu-id="80609-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80609-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80609-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80609-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80609-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80609-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80609-115">**.NET Framework wersje:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80609-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80609-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80609-116">See also</span></span>

- [<span data-ttu-id="80609-117">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="80609-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="80609-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="80609-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
