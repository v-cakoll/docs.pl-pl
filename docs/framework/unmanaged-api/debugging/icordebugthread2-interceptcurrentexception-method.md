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
ms.openlocfilehash: d87f07e6cadf8c9b5a4d8bb3063333c26e2c4ff1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379033"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="66eb9-102">ICorDebugThread2::InterceptCurrentException — Metoda</span><span class="sxs-lookup"><span data-stu-id="66eb9-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="66eb9-103">Umożliwia debugerowi przechwycenie bieżącego wyjątku w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="66eb9-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66eb9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66eb9-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66eb9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66eb9-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="66eb9-106">podczas Wskaźnik do elementu ICorDebugFrame, który reprezentuje aktywną ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="66eb9-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66eb9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66eb9-107">Remarks</span></span>  
 <span data-ttu-id="66eb9-108">`InterceptCurrentException`Metodę można wywołać między wywołaniem zwrotnym wyjątku ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) lub [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) i skojarzonym wywołaniem do [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="66eb9-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66eb9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66eb9-109">Requirements</span></span>  
 <span data-ttu-id="66eb9-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66eb9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66eb9-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66eb9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66eb9-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66eb9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66eb9-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66eb9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
