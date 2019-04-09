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
ms.openlocfilehash: 975353403a82956912fa41047253bb0dbf138502
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124127"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="f9742-102">ICorDebugManagedCallback::NameChange — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9742-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="f9742-103">Powiadamia debugera, że zmieniono nazwę domeny aplikacji lub wątku.</span><span class="sxs-lookup"><span data-stu-id="f9742-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9742-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9742-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9742-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9742-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f9742-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenie aplikacji, która albo była zmiana nazwy lub który zawiera wątku, który zmienił nazwę.</span><span class="sxs-lookup"><span data-stu-id="f9742-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="f9742-107">[in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zmienił nazwę.</span><span class="sxs-lookup"><span data-stu-id="f9742-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9742-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9742-108">Requirements</span></span>  
 <span data-ttu-id="f9742-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9742-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9742-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9742-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9742-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9742-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f9742-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f9742-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9742-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9742-113">See also</span></span>

- [<span data-ttu-id="f9742-114">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f9742-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
