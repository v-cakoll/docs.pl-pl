---
title: "ICorDebugThread2::InterceptCurrentException — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.InterceptCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 169ce528a2a6fd6ac415989437e721509d9fcda1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="0c561-102">ICorDebugThread2::InterceptCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c561-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="0c561-103">Umożliwia debugera przechwycić bieżącego wyjątku dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="0c561-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c561-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c561-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c561-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c561-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="0c561-106">[in] Wskaźnik do ICorDebugFrame reprezentujący ramki stosu aktywne.</span><span class="sxs-lookup"><span data-stu-id="0c561-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c561-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c561-107">Remarks</span></span>  
 <span data-ttu-id="0c561-108">`InterceptCurrentException` Między wyjątek wywołania zwrotnego można wywołać metody ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) lub [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) i skojarzone wywołanie [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="0c561-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c561-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c561-109">Requirements</span></span>  
 <span data-ttu-id="0c561-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c561-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c561-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c561-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c561-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c561-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c561-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c561-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
