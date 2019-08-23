---
title: ICorDebug::Terminate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de37bb34aee9b6536ff892ac30855761bcc69445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963130"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="8d239-102">ICorDebug::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d239-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="8d239-103">`ICorDebug` Kończy obiekt.</span><span class="sxs-lookup"><span data-stu-id="8d239-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d239-104">`Terminate`nie należy wywoływać do momentu odebrania wywołania zwrotnego [ICorDebugManagedCallback:: ExitProcess —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) dla wszystkich debugowanych procesów.</span><span class="sxs-lookup"><span data-stu-id="8d239-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d239-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d239-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d239-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d239-106">Remarks</span></span>  
 <span data-ttu-id="8d239-107">`Terminate`musi być wywoływana, `ICorDebug` gdy obiekt nie jest już wymagany.</span><span class="sxs-lookup"><span data-stu-id="8d239-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d239-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d239-108">Requirements</span></span>  
 <span data-ttu-id="8d239-109">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d239-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d239-110">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d239-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d239-111">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d239-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d239-112">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d239-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d239-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d239-113">See also</span></span>

- [<span data-ttu-id="8d239-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="8d239-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
