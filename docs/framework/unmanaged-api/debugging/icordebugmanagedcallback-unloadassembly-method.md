---
title: ICorDebugManagedCallback::UnloadAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef4d7993269aa606aa6b22a1544bc2d04d9e6e93
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476532"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="35855-102">ICorDebugManagedCallback::UnloadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="35855-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="35855-103">Powiadamia debugera w zestawie środowiska uruchomieniowego języka wspólnego został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="35855-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35855-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35855-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35855-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35855-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="35855-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, który zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="35855-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="35855-107">[in] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="35855-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35855-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35855-108">Remarks</span></span>  
 <span data-ttu-id="35855-109">Zestaw nie powinna być używana po to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="35855-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35855-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35855-110">Requirements</span></span>  
 <span data-ttu-id="35855-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35855-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35855-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35855-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35855-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35855-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35855-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35855-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35855-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35855-115">See also</span></span>
- [<span data-ttu-id="35855-116">LoadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="35855-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="35855-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="35855-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
