---
title: ICorDebugManagedCallback::LoadModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbf538f066058b4f80d8cfd6cdf1a79683c79be9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413420"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="3c6e7-102">ICorDebugManagedCallback::LoadModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c6e7-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="3c6e7-103">Powiadamia debuger pomyślnie załadowana wspólny moduł języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="3c6e7-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c6e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c6e7-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c6e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c6e7-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3c6e7-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, do którego został załadowany w module.</span><span class="sxs-lookup"><span data-stu-id="3c6e7-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="3c6e7-107">[in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje modułu CLR.</span><span class="sxs-lookup"><span data-stu-id="3c6e7-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c6e7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c6e7-108">Remarks</span></span>  
 <span data-ttu-id="3c6e7-109">`LoadModule` Wywołania zwrotnego zapewnia odpowiedni czas zbadać metadane dla modułu, Ustaw flagi kompilatora just in time (JIT) lub włączyć lub wyłączyć klasy ładowania wywołań zwrotnych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="3c6e7-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c6e7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c6e7-110">Requirements</span></span>  
 <span data-ttu-id="3c6e7-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c6e7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c6e7-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c6e7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c6e7-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c6e7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c6e7-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c6e7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c6e7-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c6e7-115">See Also</span></span>  
 [<span data-ttu-id="3c6e7-116">UnloadModule, metoda</span><span class="sxs-lookup"><span data-stu-id="3c6e7-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)  
 [<span data-ttu-id="3c6e7-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c6e7-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
