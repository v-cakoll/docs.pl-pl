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
ms.openlocfilehash: a892012e872dcf44512adbe0d6890812d84ed899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412597"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="5e34f-102">ICorDebugManagedCallback::UnloadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e34f-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="5e34f-103">Powiadamia debuger zestawem środowiska uruchomieniowego języka wspólnego został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="5e34f-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e34f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e34f-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e34f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e34f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5e34f-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, która zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="5e34f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="5e34f-107">[in] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="5e34f-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e34f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e34f-108">Remarks</span></span>  
 <span data-ttu-id="5e34f-109">Nie należy używać zestawu po tym wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5e34f-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e34f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e34f-110">Requirements</span></span>  
 <span data-ttu-id="5e34f-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e34f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e34f-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e34f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e34f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e34f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e34f-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e34f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e34f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e34f-115">See Also</span></span>  
 [<span data-ttu-id="5e34f-116">LoadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="5e34f-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="5e34f-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e34f-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
