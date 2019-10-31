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
ms.openlocfilehash: af2dab65629093401219f1016538b912bee4d067
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130825"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="c5cff-102">ICorDebugManagedCallback::Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5cff-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="c5cff-103">Powiadamia debugera o wygenerowanym wyjątku z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c5cff-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5cff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5cff-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5cff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5cff-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c5cff-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c5cff-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="c5cff-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c5cff-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="c5cff-108">podczas Jeśli ta wartość jest `false`, wyjątek nie został jeszcze przetworzony przez aplikację; w przeciwnym razie wyjątek jest nieobsługiwany i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="c5cff-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5cff-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5cff-109">Remarks</span></span>  
 <span data-ttu-id="c5cff-110">Konkretny wyjątek można pobrać z obiektu wątku.</span><span class="sxs-lookup"><span data-stu-id="c5cff-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5cff-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5cff-111">Requirements</span></span>  
 <span data-ttu-id="c5cff-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5cff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5cff-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5cff-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5cff-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c5cff-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5cff-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5cff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5cff-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5cff-116">See also</span></span>

- [<span data-ttu-id="c5cff-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5cff-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
