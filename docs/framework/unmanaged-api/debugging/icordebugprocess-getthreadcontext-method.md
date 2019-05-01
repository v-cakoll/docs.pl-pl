---
title: ICorDebugProcess::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28d54becc2d7cd4359c78415f25f579b968cb3f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775612"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="8b6b7-102">ICorDebugProcess::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b6b7-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="8b6b7-103">Pobiera kontekst dla danego wątku w ramach tego procesu.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b6b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b6b7-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b6b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b6b7-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8b6b7-106">[in] Identyfikator wątku, do których chcesz pobrać kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8b6b7-107">[in] Rozmiar `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="8b6b7-108">[out w] Tablica bajtów, które opisują kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="8b6b7-109">Kontekst określa z architekturą procesora, na którym wykonywany jest wątek.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b6b7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b6b7-110">Remarks</span></span>  
 <span data-ttu-id="8b6b7-111">Debuger powinien wywoływać tej metody, a nie Win32 `GetThreadContext` metody, ponieważ wątek rzeczywiście może być w stanie "przejętego", w którym zostało tymczasowo zmienione kontekst.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="8b6b7-112">Ta metoda powinna służyć tylko wtedy, gdy wątek jest w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="8b6b7-113">Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) dla wątków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="8b6b7-114">Dane zwracane to struktura kontekstu dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="8b6b7-115">Podobnie jak w przypadku Win32 `GetThreadContext` obiektu wywołującego metody, należy zainicjować `context` parametru przed wywołaniem tej metody.</span><span class="sxs-lookup"><span data-stu-id="8b6b7-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b6b7-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b6b7-116">Requirements</span></span>  
 <span data-ttu-id="8b6b7-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b6b7-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b6b7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b6b7-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b6b7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b6b7-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b6b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
