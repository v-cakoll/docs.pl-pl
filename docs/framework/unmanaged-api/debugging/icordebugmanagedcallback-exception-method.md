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
ms.openlocfilehash: 2d0461709accf1a9300c072b62bd58734cb33fb8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209815"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="36c13-102">ICorDebugManagedCallback::Exception — Metoda</span><span class="sxs-lookup"><span data-stu-id="36c13-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="36c13-103">Powiadamia debugera o wygenerowanym wyjątku z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="36c13-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36c13-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36c13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36c13-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="36c13-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="36c13-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="36c13-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym został zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="36c13-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="36c13-108">podczas Jeśli ta wartość jest `false` , wyjątek nie został jeszcze przetworzony przez aplikację; w przeciwnym razie wyjątek jest nieobsługiwany i zakończy proces.</span><span class="sxs-lookup"><span data-stu-id="36c13-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36c13-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36c13-109">Remarks</span></span>  
 <span data-ttu-id="36c13-110">Konkretny wyjątek można pobrać z obiektu wątku.</span><span class="sxs-lookup"><span data-stu-id="36c13-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c13-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36c13-111">Requirements</span></span>  
 <span data-ttu-id="36c13-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36c13-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c13-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36c13-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36c13-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="36c13-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36c13-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c13-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c13-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36c13-116">See also</span></span>

- [<span data-ttu-id="36c13-117">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="36c13-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
