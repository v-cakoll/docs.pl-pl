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
ms.openlocfilehash: 31a554fc57611f4abd5322fdc0c147e5dc110fb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654948"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="d3bde-102">ICorDebugManagedCallback::DebuggerError — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3bde-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="d3bde-103">Powiadamia debuger wystąpił błąd podczas próby obsłużyć zdarzenie z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d3bde-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3bde-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3bde-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3bde-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3bde-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d3bde-106">[in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d3bde-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="d3bde-107">[in] Wartość HRESULT, który został zwrócony z programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d3bde-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="d3bde-108">[in] Liczba całkowita określająca błąd środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d3bde-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3bde-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3bde-109">Remarks</span></span>  
 <span data-ttu-id="d3bde-110">Proces mógł być umieszczony w trybie przekazywania, w zależności od charakteru błędu.</span><span class="sxs-lookup"><span data-stu-id="d3bde-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="d3bde-111">`DebugError` Wywołania zwrotnego wskazuje, że debugowania usługi zostały wyłączone z powodu błędu, dzięki czemu debugery powinny udostępniać komunikat o błędzie dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d3bde-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="d3bde-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) będzie bezpieczne połączenie, ale wszystkie inne metody, w tym [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), nie powinna być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d3bde-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="d3bde-113">Debuger powinien użyć systemu operacyjnego urządzenia dla zakończenie procesów.</span><span class="sxs-lookup"><span data-stu-id="d3bde-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3bde-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3bde-114">Requirements</span></span>  
 <span data-ttu-id="d3bde-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3bde-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3bde-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3bde-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3bde-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3bde-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3bde-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3bde-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3bde-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3bde-119">See also</span></span>
- [<span data-ttu-id="d3bde-120">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3bde-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
