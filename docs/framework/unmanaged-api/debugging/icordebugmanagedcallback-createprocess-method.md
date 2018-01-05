---
title: "ICorDebugManagedCallback::CreateProcess — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14c2219f1a328b3e48380c7c31f705b79da3b1ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="22310-102">ICorDebugManagedCallback::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="22310-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="22310-103">Powiadamia debuger został dołączony proces lub uruchomiony po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="22310-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22310-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="22310-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22310-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22310-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="22310-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który jest dołączony lub został rozpoczęty.</span><span class="sxs-lookup"><span data-stu-id="22310-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22310-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22310-107">Remarks</span></span>  
 <span data-ttu-id="22310-108">Ta metoda nie jest wywoływany, dopóki nie została zainicjowana przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="22310-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="22310-109">Większość [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody zwróci CORDBG_E_NOTREADY przed `CreateProcess` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="22310-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22310-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22310-110">Requirements</span></span>  
 <span data-ttu-id="22310-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22310-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22310-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22310-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22310-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22310-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22310-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22310-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22310-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22310-115">See Also</span></span>  
 [<span data-ttu-id="22310-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="22310-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
