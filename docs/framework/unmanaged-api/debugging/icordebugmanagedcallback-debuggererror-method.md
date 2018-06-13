---
title: ICorDebugManagedCallback::DebuggerError — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 436be84ad91bb20bfd88a51f2d6c2b760c4a4c3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420140"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="d3db4-102">ICorDebugManagedCallback::DebuggerError — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3db4-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="d3db4-103">Powiadamia debugera wystąpił błąd podczas próby Obsługa zdarzenia z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d3db4-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3db4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3db4-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3db4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3db4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d3db4-106">[in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d3db4-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="d3db4-107">[in] Wartość HRESULT zwrócony przez program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d3db4-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="d3db4-108">[in] Liczba całkowita określająca błąd środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d3db4-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3db4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3db4-109">Remarks</span></span>  
 <span data-ttu-id="d3db4-110">Proces może być umieszczona w trybie przekazujące, w zależności od charakteru błędu.</span><span class="sxs-lookup"><span data-stu-id="d3db4-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="d3db4-111">`DebugError` Wywołania zwrotnego wskazuje, że usług debugowania zostały wyłączone z powodu błędu, więc debugery należy udostępnić komunikat o błędzie dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d3db4-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="d3db4-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) będzie bezpieczne połączenie, ale wszystkie inne metody, w tym [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), nie należy wywoływać.</span><span class="sxs-lookup"><span data-stu-id="d3db4-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="d3db4-113">Do zakończenia procesów debuger należy używać systemu operacyjnego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="d3db4-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3db4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3db4-114">Requirements</span></span>  
 <span data-ttu-id="d3db4-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3db4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3db4-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3db4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3db4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3db4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3db4-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3db4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3db4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3db4-119">See Also</span></span>  
 [<span data-ttu-id="d3db4-120">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3db4-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
