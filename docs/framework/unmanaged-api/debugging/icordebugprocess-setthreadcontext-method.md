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
ms.openlocfilehash: c9ed79eb799971dfcbc9fd787cd0290795f79d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="c85bf-102">ICorDebugProcess::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="c85bf-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="c85bf-103">Ustawia kontekst dla danego wątku, w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="c85bf-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c85bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c85bf-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c85bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c85bf-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c85bf-106">[in] Identyfikator wątku, który można ustawić kontekstu.</span><span class="sxs-lookup"><span data-stu-id="c85bf-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c85bf-107">[in] Rozmiar `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c85bf-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="c85bf-108">[in] Tablica bajtów, które opisują kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="c85bf-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="c85bf-109">Kontekst określa architektury procesora, na którym jest wykonywany wątku.</span><span class="sxs-lookup"><span data-stu-id="c85bf-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c85bf-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c85bf-110">Remarks</span></span>  
 <span data-ttu-id="c85bf-111">Debuger powinien wywoływać tej metody zamiast Win32 `SetThreadContext` działać, ponieważ wątek faktycznie może być w stanie "hijacked", w którym zostało tymczasowo zmienione kontekst.</span><span class="sxs-lookup"><span data-stu-id="c85bf-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="c85bf-112">Tej metody należy użyć tylko wtedy, gdy wątek jest w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="c85bf-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="c85bf-113">Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) wątków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="c85bf-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="c85bf-114">Nigdy nie powinien konieczne zmodyfikowanie kontekst wątku podczas zdarzenia debugowania poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="c85bf-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="c85bf-115">Dane przekazane musi być strukturą kontekst dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="c85bf-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="c85bf-116">Ta metoda może uszkodzić środowiska uruchomieniowego, użycie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="c85bf-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c85bf-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c85bf-117">Requirements</span></span>  
 <span data-ttu-id="c85bf-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c85bf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c85bf-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c85bf-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c85bf-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c85bf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c85bf-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c85bf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
