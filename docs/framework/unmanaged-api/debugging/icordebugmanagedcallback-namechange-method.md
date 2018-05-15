---
title: ICorDebugManagedCallback::NameChange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a7ef478fed697f4152a6348931ddf3b4b4b2885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="58403-102">ICorDebugManagedCallback::NameChange — Metoda</span><span class="sxs-lookup"><span data-stu-id="58403-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="58403-103">Powiadamia debugera, że nazwa domeny aplikacji lub wątek został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="58403-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58403-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58403-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58403-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58403-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="58403-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenie aplikacji, które albo była zmiana nazwy lub które zawiera wątku, który miał zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="58403-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="58403-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku, który miał zmiany nazwy.</span><span class="sxs-lookup"><span data-stu-id="58403-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58403-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58403-108">Requirements</span></span>  
 <span data-ttu-id="58403-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58403-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58403-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58403-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58403-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58403-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58403-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58403-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58403-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58403-113">See Also</span></span>  
 [<span data-ttu-id="58403-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="58403-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
