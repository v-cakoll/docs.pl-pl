---
title: ICorDebugThread2::InterceptCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f417fcd001d9e442ae518dbcd9df26eecb6efae9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421977"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="efb96-102">ICorDebugThread2::InterceptCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="efb96-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="efb96-103">Umożliwia debugera przechwycić bieżącego wyjątku dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="efb96-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efb96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efb96-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efb96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efb96-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="efb96-106">[in] Wskaźnik do ICorDebugFrame reprezentujący ramki stosu aktywne.</span><span class="sxs-lookup"><span data-stu-id="efb96-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efb96-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efb96-107">Remarks</span></span>  
 <span data-ttu-id="efb96-108">`InterceptCurrentException` Między wyjątek wywołania zwrotnego można wywołać metody ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) lub [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) i skojarzone wywołanie [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="efb96-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efb96-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efb96-109">Requirements</span></span>  
 <span data-ttu-id="efb96-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efb96-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efb96-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efb96-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efb96-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efb96-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efb96-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efb96-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
