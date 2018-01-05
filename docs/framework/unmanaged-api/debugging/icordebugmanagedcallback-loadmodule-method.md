---
title: "ICorDebugManagedCallback::LoadModule — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d17001db68043f5d46a90738a8ad3e0635de762
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="c02f1-102">ICorDebugManagedCallback::LoadModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="c02f1-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="c02f1-103">Powiadamia debuger pomyślnie załadowana wspólny moduł języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="c02f1-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c02f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c02f1-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c02f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c02f1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c02f1-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, do którego został załadowany w module.</span><span class="sxs-lookup"><span data-stu-id="c02f1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="c02f1-107">[in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje modułu CLR.</span><span class="sxs-lookup"><span data-stu-id="c02f1-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c02f1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c02f1-108">Remarks</span></span>  
 <span data-ttu-id="c02f1-109">`LoadModule` Wywołania zwrotnego zapewnia odpowiedni czas zbadać metadane dla modułu, Ustaw flagi kompilatora just in time (JIT) lub włączyć lub wyłączyć klasy ładowania wywołań zwrotnych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="c02f1-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c02f1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c02f1-110">Requirements</span></span>  
 <span data-ttu-id="c02f1-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c02f1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c02f1-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c02f1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c02f1-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c02f1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c02f1-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c02f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c02f1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c02f1-115">See Also</span></span>  
 [<span data-ttu-id="c02f1-116">UnloadModule, metoda</span><span class="sxs-lookup"><span data-stu-id="c02f1-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [<span data-ttu-id="c02f1-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c02f1-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
