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
ms.openlocfilehash: 0eacb4b0a06fbe086935b59eba7d33135b6bef19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759710"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="703bf-102">ICorDebugManagedCallback::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="703bf-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="703bf-103">Powiadamia debuger został dołączony proces lub uruchomiona po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="703bf-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="703bf-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="703bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="703bf-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="703bf-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który jest dołączony lub pracy.</span><span class="sxs-lookup"><span data-stu-id="703bf-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="703bf-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="703bf-107">Remarks</span></span>  
 <span data-ttu-id="703bf-108">Ta metoda nie jest wywoływana, dopóki nie został zainicjowany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="703bf-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="703bf-109">Większość [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody zwróci CORDBG_E_NOTREADY przed `CreateProcess` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="703bf-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="703bf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="703bf-110">Requirements</span></span>  
 <span data-ttu-id="703bf-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703bf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703bf-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="703bf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="703bf-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="703bf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="703bf-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703bf-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="703bf-115">See also</span></span>

- [<span data-ttu-id="703bf-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="703bf-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
