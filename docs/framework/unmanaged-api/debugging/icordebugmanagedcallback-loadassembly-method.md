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
ms.openlocfilehash: 2143524b92ca34299877fe935ae5a603c3e86563
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540510"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="bd61f-102">ICorDebugManagedCallback::LoadAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd61f-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>
<span data-ttu-id="bd61f-103">Powiadamia debugera w zestawie środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego został pomyślnie załadowany.</span><span class="sxs-lookup"><span data-stu-id="bd61f-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd61f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd61f-104">Syntax</span></span>  
  
```  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd61f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd61f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bd61f-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której zestaw został załadowany.</span><span class="sxs-lookup"><span data-stu-id="bd61f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="bd61f-107">[in] Wskaźnik do obiektu ICorDebugAssembly, który reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="bd61f-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd61f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd61f-108">Requirements</span></span>  
 <span data-ttu-id="bd61f-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd61f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd61f-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd61f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd61f-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd61f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd61f-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd61f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd61f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd61f-113">See also</span></span>
- [<span data-ttu-id="bd61f-114">UnloadAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="bd61f-114">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="bd61f-115">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd61f-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
