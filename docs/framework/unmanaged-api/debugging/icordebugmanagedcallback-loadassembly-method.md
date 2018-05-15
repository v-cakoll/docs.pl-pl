---
title: ICorDebugManagedCallback::LoadAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1d05914004d3c1fcc5ff109e854d01661367835
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="be7e0-102">ICorDebugManagedCallback::LoadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="be7e0-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="be7e0-103">Powiadamia debugera, czy został pomyślnie załadowany z zestawem środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="be7e0-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be7e0-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be7e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be7e0-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="be7e0-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, w której zestaw został załadowany.</span><span class="sxs-lookup"><span data-stu-id="be7e0-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="be7e0-107">[in] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="be7e0-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be7e0-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be7e0-108">Requirements</span></span>  
 <span data-ttu-id="be7e0-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be7e0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be7e0-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be7e0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be7e0-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be7e0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be7e0-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be7e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7e0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be7e0-113">See Also</span></span>  
 [<span data-ttu-id="be7e0-114">UnloadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="be7e0-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)  
 [<span data-ttu-id="be7e0-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="be7e0-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
