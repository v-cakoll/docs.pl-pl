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
ms.openlocfilehash: c33f287cf7ccadeb75ba0bbccf9118aeedc1f942
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607439"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="cb6f4-102">ICorDebugManagedCallback::NameChange — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb6f4-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="cb6f4-103">Powiadamia debugera, że zmieniono nazwę domeny aplikacji lub wątku.</span><span class="sxs-lookup"><span data-stu-id="cb6f4-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb6f4-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb6f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb6f4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cb6f4-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenie aplikacji, która albo była zmiana nazwy lub który zawiera wątku, który zmienił nazwę.</span><span class="sxs-lookup"><span data-stu-id="cb6f4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cb6f4-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zmienił nazwę.</span><span class="sxs-lookup"><span data-stu-id="cb6f4-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb6f4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb6f4-108">Requirements</span></span>  
 <span data-ttu-id="cb6f4-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb6f4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb6f4-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb6f4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb6f4-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb6f4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb6f4-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb6f4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6f4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb6f4-113">See also</span></span>
- [<span data-ttu-id="cb6f4-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb6f4-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
