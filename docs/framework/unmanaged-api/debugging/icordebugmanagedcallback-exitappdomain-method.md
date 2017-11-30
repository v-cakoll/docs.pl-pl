---
title: "ICorDebugManagedCallback::ExitAppDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ExitAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07f76d8add6c8b0e44eba241b7787b8e8a2de570
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="e1903-102">ICorDebugManagedCallback::ExitAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1903-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="e1903-103">Powiadamia debuger zakończył domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1903-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1903-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1903-104">Syntax</span></span>  
  
```  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1903-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1903-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e1903-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który zawiera domeny danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1903-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="e1903-107">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, który został zakończony.</span><span class="sxs-lookup"><span data-stu-id="e1903-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1903-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1903-108">Requirements</span></span>  
 <span data-ttu-id="e1903-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1903-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1903-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1903-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1903-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1903-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1903-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1903-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1903-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1903-113">See Also</span></span>  
 [<span data-ttu-id="e1903-114">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="e1903-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
