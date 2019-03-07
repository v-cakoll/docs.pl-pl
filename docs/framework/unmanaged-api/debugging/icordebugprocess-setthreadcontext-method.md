---
title: ICorDebugProcess::SetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e281022cd7bc9b2095fdbd3964061b811ef60e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496966"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="9192a-102">ICorDebugProcess::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="9192a-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="9192a-103">Ustawia kontekst dla danego wątku w ramach tego procesu.</span><span class="sxs-lookup"><span data-stu-id="9192a-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9192a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9192a-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9192a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9192a-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="9192a-106">[in] Identyfikator wątku, do których chcesz ustawić kontekst.</span><span class="sxs-lookup"><span data-stu-id="9192a-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="9192a-107">[in] Rozmiar `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9192a-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="9192a-108">[in] Tablica bajtów, które opisują kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="9192a-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="9192a-109">Kontekst określa z architekturą procesora, na którym wykonywany jest wątek.</span><span class="sxs-lookup"><span data-stu-id="9192a-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9192a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9192a-110">Remarks</span></span>  
 <span data-ttu-id="9192a-111">Debuger powinien wywoływać tej metody, a nie Win32 `SetThreadContext` działać, ponieważ wątek rzeczywiście może być w stanie "przejętego", w którym zostało tymczasowo zmienione kontekst.</span><span class="sxs-lookup"><span data-stu-id="9192a-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="9192a-112">Ta metoda powinna służyć tylko wtedy, gdy wątek jest w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="9192a-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="9192a-113">Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) dla wątków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="9192a-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="9192a-114">Nigdy nie należy modyfikować kontekst wątku podczas zdarzenia debugowania poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="9192a-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="9192a-115">Dane przekazywane musi być strukturą kontekstu dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="9192a-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="9192a-116">Ta metoda może uszkodzić środowisko wykonawcze, jeśli niepoprawnie.</span><span class="sxs-lookup"><span data-stu-id="9192a-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9192a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9192a-117">Requirements</span></span>  
 <span data-ttu-id="9192a-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9192a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9192a-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9192a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9192a-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9192a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9192a-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9192a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
