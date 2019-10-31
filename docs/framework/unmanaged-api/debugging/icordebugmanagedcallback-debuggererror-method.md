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
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137370"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="d452f-102">ICorDebugManagedCallback::DebuggerError — Metoda</span><span class="sxs-lookup"><span data-stu-id="d452f-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="d452f-103">Powiadamia debuger, że wystąpił błąd podczas próby obsłużenia zdarzenia z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="d452f-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d452f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d452f-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d452f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d452f-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d452f-106">podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d452f-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="d452f-107">podczas Wartość HRESULT, która została zwrócona przez program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d452f-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="d452f-108">podczas Liczba całkowita, która określa błąd CLR.</span><span class="sxs-lookup"><span data-stu-id="d452f-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d452f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d452f-109">Remarks</span></span>  
 <span data-ttu-id="d452f-110">Proces może być umieszczony w trybie przekazywania, w zależności od charakteru błędu.</span><span class="sxs-lookup"><span data-stu-id="d452f-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="d452f-111">Wywołanie zwrotne `DebugError` wskazuje, że usługi debugowania zostały wyłączone z powodu błędu, dlatego debugery powinny udostępnić komunikat o błędzie dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d452f-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="d452f-112">[ICorDebugProcess:: GetId —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) będzie bezpieczne do wywołania, ale wszystkie inne metody, w tym [ICorDebug:: terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), nie powinny być wywoływane.</span><span class="sxs-lookup"><span data-stu-id="d452f-112">[ICorDebugProcess::GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="d452f-113">Debuger powinien używać obiektów systemu operacyjnego do kończenia procesów.</span><span class="sxs-lookup"><span data-stu-id="d452f-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d452f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d452f-114">Requirements</span></span>  
 <span data-ttu-id="d452f-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d452f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d452f-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d452f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d452f-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d452f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d452f-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d452f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d452f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d452f-119">See also</span></span>

- [<span data-ttu-id="d452f-120">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d452f-120">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
