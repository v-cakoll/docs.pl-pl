---
title: "ICorDebugManagedCallback::UnloadAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 731615729f680bae4c4b8517de4a3e522d4acae2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="42218-102">ICorDebugManagedCallback::UnloadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="42218-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="42218-103">Powiadamia debuger zestawem środowiska uruchomieniowego języka wspólnego został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="42218-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42218-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42218-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42218-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42218-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="42218-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, która zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="42218-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="42218-107">[in] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="42218-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42218-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42218-108">Remarks</span></span>  
 <span data-ttu-id="42218-109">Nie należy używać zestawu po tym wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="42218-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42218-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42218-110">Requirements</span></span>  
 <span data-ttu-id="42218-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42218-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42218-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42218-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42218-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42218-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42218-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42218-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42218-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42218-115">See Also</span></span>  
 [<span data-ttu-id="42218-116">LoadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="42218-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)  
 [<span data-ttu-id="42218-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="42218-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
