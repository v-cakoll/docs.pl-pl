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
ms.openlocfilehash: 0c3059697014cea33081f6cb81b9d93c7d028c2e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777467"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="2157b-102">ICorDebugManagedCallback::CreateProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="2157b-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="2157b-103">Powiadamia debuger, gdy proces został dołączony lub uruchomiony po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="2157b-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2157b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2157b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2157b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2157b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="2157b-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który został dołączony lub uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="2157b-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2157b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2157b-107">Remarks</span></span>  
 <span data-ttu-id="2157b-108">Ta metoda nie jest wywoływana do momentu zainicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="2157b-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="2157b-109">Większość metod [ICorDebug](icordebug-interface.md) zwróci CORDBG_E_NOTREADY przed wywołaniem zwrotnym `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="2157b-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2157b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2157b-110">Requirements</span></span>  
 <span data-ttu-id="2157b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2157b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2157b-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2157b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2157b-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2157b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2157b-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2157b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2157b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2157b-115">See also</span></span>

- [<span data-ttu-id="2157b-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="2157b-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
