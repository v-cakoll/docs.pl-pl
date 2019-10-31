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
ms.openlocfilehash: d773368c85fd42fd169109cf1c7e6635705ebb7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090229"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="e5bf0-102">ICorDebugManagedCallback::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5bf0-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="e5bf0-103">Powiadamia debuger, gdy proces został dołączony lub uruchomiony po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e5bf0-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5bf0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5bf0-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5bf0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5bf0-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="e5bf0-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który został dołączony lub uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="e5bf0-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5bf0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5bf0-107">Remarks</span></span>  
 <span data-ttu-id="e5bf0-108">Ta metoda nie jest wywoływana do momentu zainicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e5bf0-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="e5bf0-109">Większość metod [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) zwróci CORDBG_E_NOTREADY przed wywołaniem zwrotnym `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="e5bf0-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5bf0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5bf0-110">Requirements</span></span>  
 <span data-ttu-id="e5bf0-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5bf0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5bf0-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5bf0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5bf0-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5bf0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5bf0-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5bf0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5bf0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5bf0-115">See also</span></span>

- [<span data-ttu-id="e5bf0-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5bf0-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
