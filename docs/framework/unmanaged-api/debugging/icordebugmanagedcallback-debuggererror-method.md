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
ms.openlocfilehash: 8f3697f8b193319ebb7b155ad79b8ec25a0a2266
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205277"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a><span data-ttu-id="20d91-102">ICorDebugManagedCallback::DebuggerError — Metoda</span><span class="sxs-lookup"><span data-stu-id="20d91-102">ICorDebugManagedCallback::DebuggerError Method</span></span>
<span data-ttu-id="20d91-103">Powiadamia debuger, że wystąpił błąd podczas próby obsłużenia zdarzenia z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="20d91-103">Notifies the debugger that an error has occurred while attempting to handle an event from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20d91-104">Syntax</span></span>  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20d91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20d91-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="20d91-106">podczas Wskaźnik do obiektu "ICorDebugProcess", który reprezentuje proces, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="20d91-106">[in] A pointer to an "ICorDebugProcess" object that represents the process in which the event occurred.</span></span>  
  
 `errorHR`  
 <span data-ttu-id="20d91-107">podczas Wartość HRESULT, która została zwrócona przez program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="20d91-107">[in] The HRESULT value that was returned from the event handler.</span></span>  
  
 `errorCode`  
 <span data-ttu-id="20d91-108">podczas Liczba całkowita, która określa błąd CLR.</span><span class="sxs-lookup"><span data-stu-id="20d91-108">[in] An integer that specifies the CLR error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20d91-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20d91-109">Remarks</span></span>  
 <span data-ttu-id="20d91-110">Proces może być umieszczony w trybie przekazywania, w zależności od charakteru błędu.</span><span class="sxs-lookup"><span data-stu-id="20d91-110">The process may be placed into pass-through mode, depending on the nature of the error.</span></span>  
  
 <span data-ttu-id="20d91-111">`DebugError`Wywołanie zwrotne wskazuje, że usługi debugowania zostały wyłączone z powodu błędu, dlatego debugery powinny udostępnić komunikat o błędzie dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="20d91-111">The `DebugError` callback indicates that debugging services have been disabled due to an error, so debuggers should make the error message available to the user.</span></span> <span data-ttu-id="20d91-112">[ICorDebugProcess:: GetId —](icordebugprocess-getid-method.md) będzie bezpieczne do wywołania, ale wszystkie inne metody, w tym [ICorDebug:: terminate](icordebug-terminate-method.md), nie powinny być wywoływane.</span><span class="sxs-lookup"><span data-stu-id="20d91-112">[ICorDebugProcess::GetID](icordebugprocess-getid-method.md) will be safe to call, but all other methods, including [ICorDebug::Terminate](icordebug-terminate-method.md), should not be called.</span></span> <span data-ttu-id="20d91-113">Debuger powinien używać obiektów systemu operacyjnego do kończenia procesów.</span><span class="sxs-lookup"><span data-stu-id="20d91-113">The debugger should use operating-system facilities for terminating processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20d91-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20d91-114">Requirements</span></span>  
 <span data-ttu-id="20d91-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20d91-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20d91-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20d91-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20d91-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20d91-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20d91-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20d91-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d91-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20d91-119">See also</span></span>

- [<span data-ttu-id="20d91-120">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="20d91-120">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
