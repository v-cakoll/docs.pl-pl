---
title: ICorDebugManagedCallback::CreateProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda214200ca4c3837ad89ed14887ef6b09af7d30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160371"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="299a6-102">ICorDebugManagedCallback::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="299a6-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="299a6-103">Powiadamia debuger został dołączony proces lub uruchomiona po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="299a6-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="299a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="299a6-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="299a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="299a6-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="299a6-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który jest dołączony lub pracy.</span><span class="sxs-lookup"><span data-stu-id="299a6-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="299a6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="299a6-107">Remarks</span></span>  
 <span data-ttu-id="299a6-108">Ta metoda nie jest wywoływana, dopóki nie został zainicjowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="299a6-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="299a6-109">Większość [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody zwróci CORDBG_E_NOTREADY przed `CreateProcess` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="299a6-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="299a6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="299a6-110">Requirements</span></span>  
 <span data-ttu-id="299a6-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="299a6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="299a6-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="299a6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="299a6-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="299a6-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="299a6-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="299a6-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="299a6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="299a6-115">See also</span></span>

- [<span data-ttu-id="299a6-116">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="299a6-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
