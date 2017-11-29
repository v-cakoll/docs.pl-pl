---
title: "ICorDebugProcess::SetThreadContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 70368602672e06dc3a5aaf4f2f4bc7632c5a9a79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="6765d-102">ICorDebugProcess::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="6765d-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="6765d-103">Ustawia kontekst dla danego wątku, w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="6765d-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6765d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6765d-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6765d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6765d-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="6765d-106">[in] Identyfikator wątku, który można ustawić kontekstu.</span><span class="sxs-lookup"><span data-stu-id="6765d-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6765d-107">[in] Rozmiar `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6765d-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="6765d-108">[in] Tablica bajtów, które opisują kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="6765d-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="6765d-109">Kontekst określa architektury procesora, na którym jest wykonywany wątku.</span><span class="sxs-lookup"><span data-stu-id="6765d-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6765d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6765d-110">Remarks</span></span>  
 <span data-ttu-id="6765d-111">Debuger powinien wywoływać tej metody zamiast Win32 `SetThreadContext` działać, ponieważ wątek faktycznie może być w stanie "hijacked", w którym zostało tymczasowo zmienione kontekst.</span><span class="sxs-lookup"><span data-stu-id="6765d-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="6765d-112">Tej metody należy użyć tylko wtedy, gdy wątek jest w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="6765d-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="6765d-113">Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) wątków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="6765d-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="6765d-114">Nigdy nie powinien konieczne zmodyfikowanie kontekst wątku podczas zdarzenia debugowania poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="6765d-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="6765d-115">Dane przekazane musi być strukturą kontekst dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="6765d-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="6765d-116">Ta metoda może uszkodzić środowiska uruchomieniowego, użycie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="6765d-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6765d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6765d-117">Requirements</span></span>  
 <span data-ttu-id="6765d-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6765d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6765d-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6765d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6765d-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6765d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6765d-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6765d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
