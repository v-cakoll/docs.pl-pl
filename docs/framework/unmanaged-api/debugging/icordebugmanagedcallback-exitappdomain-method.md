---
title: ICorDebugManagedCallback::ExitAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aed6ccd938761385aafd21802829bd741847b4ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110243"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="06c70-102">ICorDebugManagedCallback::ExitAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="06c70-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="06c70-103">Powiadamia debuger zakończył domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06c70-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06c70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06c70-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06c70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06c70-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="06c70-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który zawiera domenę danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06c70-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="06c70-107">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, który został zakończony.</span><span class="sxs-lookup"><span data-stu-id="06c70-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06c70-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06c70-108">Requirements</span></span>  
 <span data-ttu-id="06c70-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06c70-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06c70-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06c70-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06c70-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06c70-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="06c70-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="06c70-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="06c70-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06c70-113">See also</span></span>

- [<span data-ttu-id="06c70-114">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="06c70-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
