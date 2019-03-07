---
title: ICorDebugManagedCallback::Exception — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e985d82fcce404e15344f2277d27a6aab45f9efc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472510"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="8eab8-102">ICorDebugManagedCallback::Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="8eab8-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="8eab8-103">Powiadamia debuger zgłoszony wyjątek z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="8eab8-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eab8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8eab8-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eab8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eab8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8eab8-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8eab8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8eab8-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8eab8-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="8eab8-108">[in] Jeśli ta wartość jest `false`, wyjątek jeszcze nie zostały przetworzone przez aplikację; w przeciwnym razie, wyjątek nie jest obsługiwana i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="8eab8-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eab8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8eab8-109">Remarks</span></span>  
 <span data-ttu-id="8eab8-110">Określony wyjątek, mogą być pobierane z obiektu wątku.</span><span class="sxs-lookup"><span data-stu-id="8eab8-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eab8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8eab8-111">Requirements</span></span>  
 <span data-ttu-id="8eab8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eab8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eab8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8eab8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eab8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8eab8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eab8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eab8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eab8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8eab8-116">See also</span></span>
- [<span data-ttu-id="8eab8-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8eab8-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
