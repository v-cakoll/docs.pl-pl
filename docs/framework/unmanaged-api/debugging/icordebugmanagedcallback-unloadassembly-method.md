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
ms.openlocfilehash: 93d44006dd6652a8d34c23209eb957b23064f976
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704007"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="16c24-102">ICorDebugManagedCallback::UnloadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="16c24-102">ICorDebugManagedCallback::UnloadAssembly Method</span></span>
<span data-ttu-id="16c24-103">Powiadamia debugera w zestawie środowiska uruchomieniowego języka wspólnego został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="16c24-103">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16c24-104">Syntax</span></span>  
  
```  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16c24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16c24-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="16c24-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, który zawiera zestaw.</span><span class="sxs-lookup"><span data-stu-id="16c24-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="16c24-107">[in] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="16c24-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16c24-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16c24-108">Remarks</span></span>  
 <span data-ttu-id="16c24-109">Zestaw nie powinna być używana po to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="16c24-109">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c24-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16c24-110">Requirements</span></span>  
 <span data-ttu-id="16c24-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c24-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c24-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16c24-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16c24-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16c24-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c24-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c24-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c24-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16c24-115">See also</span></span>
- [<span data-ttu-id="16c24-116">LoadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="16c24-116">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="16c24-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="16c24-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
