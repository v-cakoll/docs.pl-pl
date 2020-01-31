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
ms.openlocfilehash: c25a03ef5bbba18da31787c911f83a1348badd4b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791454"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="86b1f-102">ICorDebugThread2::InterceptCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="86b1f-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="86b1f-103">Umożliwia debugerowi przechwycenie bieżącego wyjątku w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="86b1f-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86b1f-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86b1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86b1f-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="86b1f-106">podczas Wskaźnik do elementu ICorDebugFrame, który reprezentuje aktywną ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="86b1f-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86b1f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86b1f-107">Remarks</span></span>  
 <span data-ttu-id="86b1f-108">Metodę `InterceptCurrentException` można wywołać między wywołaniem zwrotnym wyjątku ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) lub [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) i skojarzonym wywołaniem do [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="86b1f-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86b1f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86b1f-109">Requirements</span></span>  
 <span data-ttu-id="86b1f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86b1f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86b1f-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86b1f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86b1f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="86b1f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86b1f-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86b1f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
