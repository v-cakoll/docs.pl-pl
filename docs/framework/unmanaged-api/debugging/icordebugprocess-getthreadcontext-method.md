---
title: "ICorDebugProcess::GetThreadContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9cb2b0be2954c041b364f9c85c40570a9f04421f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="d48c5-102">ICorDebugProcess::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="d48c5-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="d48c5-103">Pobiera kontekst dla danego wątku, w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="d48c5-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d48c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d48c5-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d48c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d48c5-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d48c5-106">[in] Identyfikator wątku, który można pobrać kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d48c5-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d48c5-107">[in] Rozmiar `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d48c5-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="d48c5-108">[w, out] Tablica bajtów, które opisują kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="d48c5-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="d48c5-109">Kontekst określa architektury procesora, na którym jest wykonywany wątku.</span><span class="sxs-lookup"><span data-stu-id="d48c5-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d48c5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d48c5-110">Remarks</span></span>  
 <span data-ttu-id="d48c5-111">Debuger powinien wywoływać tej metody zamiast Win32 `GetThreadContext` metody, ponieważ wątek faktycznie może być w stanie "hijacked", w którym zostało tymczasowo zmienione kontekst.</span><span class="sxs-lookup"><span data-stu-id="d48c5-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="d48c5-112">Tej metody należy użyć tylko wtedy, gdy wątek jest w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="d48c5-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="d48c5-113">Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) wątków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d48c5-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="d48c5-114">Dane zwrócone to struktura kontekst dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="d48c5-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="d48c5-115">Tak jak w przypadku środowiska Win32 `GetThreadContext` metody, wywołujący powinien zainicjować `context` parametru przed wywołaniem tej metody.</span><span class="sxs-lookup"><span data-stu-id="d48c5-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d48c5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d48c5-116">Requirements</span></span>  
 <span data-ttu-id="d48c5-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d48c5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d48c5-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d48c5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d48c5-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d48c5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d48c5-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d48c5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
