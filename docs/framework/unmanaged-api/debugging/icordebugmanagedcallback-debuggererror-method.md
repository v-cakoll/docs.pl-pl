---
title: "ICorDebugManagedCallback::DebuggerError — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4eb16762d2a0db01c3cc921712a89995e0c87c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="ff41b-102">ICorDebugManagedCallback::DebuggerError — Metoda</span><span class="sxs-lookup"><span data-stu-id="ff41b-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="ff41b-103">Powiadamia debugera wystąpił błąd podczas próby Obsługa zdarzenia z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ff41b-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff41b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff41b-104">Syntax</span></span>  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff41b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff41b-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="ff41b-106">[in] Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ff41b-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="ff41b-107">[in] Wartość HRESULT zwrócony przez program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ff41b-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="ff41b-108">[in] Liczba całkowita określająca błąd środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ff41b-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff41b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff41b-109">Remarks</span></span>  
 <span data-ttu-id="ff41b-110">Proces może być umieszczona w trybie przekazujące, w zależności od charakteru błędu.</span><span class="sxs-lookup"><span data-stu-id="ff41b-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="ff41b-111">`DebugError` Wywołania zwrotnego wskazuje, że usług debugowania zostały wyłączone z powodu błędu, więc debugery należy udostępnić komunikat o błędzie dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ff41b-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="ff41b-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) będzie bezpieczne połączenie, ale wszystkie inne metody, w tym [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), nie należy wywoływać.</span><span class="sxs-lookup"><span data-stu-id="ff41b-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="ff41b-113">Do zakończenia procesów debuger należy używać systemu operacyjnego urządzenia.</span><span class="sxs-lookup"><span data-stu-id="ff41b-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff41b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff41b-114">Requirements</span></span>  
 <span data-ttu-id="ff41b-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff41b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff41b-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff41b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff41b-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff41b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff41b-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff41b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff41b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff41b-119">See Also</span></span>  
 [<span data-ttu-id="ff41b-120">ICorDebugManagedCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="ff41b-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
