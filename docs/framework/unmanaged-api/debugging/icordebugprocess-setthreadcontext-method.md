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
ms.openlocfilehash: 66d544bbc0511ea76565376c8f10294f1758026b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792571"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="7be6e-102">ICorDebugProcess::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="7be6e-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="7be6e-103">Ustawia kontekst dla danego wątku w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="7be6e-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7be6e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7be6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7be6e-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="7be6e-106">podczas Identyfikator wątku, dla którego ma zostać ustawiony kontekst.</span><span class="sxs-lookup"><span data-stu-id="7be6e-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7be6e-107">podczas Rozmiar tablicy `context`.</span><span class="sxs-lookup"><span data-stu-id="7be6e-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="7be6e-108">podczas Tablica bajtów opisująca kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="7be6e-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="7be6e-109">Kontekst określa architekturę procesora, w którym wykonywany jest wątek.</span><span class="sxs-lookup"><span data-stu-id="7be6e-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7be6e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7be6e-110">Remarks</span></span>  
 <span data-ttu-id="7be6e-111">Debuger powinien wywołać tę metodę, a nie funkcję Win32 `SetThreadContext`, ponieważ wątek może być w stanie "przejęte", w którym jego kontekst został tymczasowo zmieniony.</span><span class="sxs-lookup"><span data-stu-id="7be6e-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="7be6e-112">Ta metoda powinna być używana tylko wtedy, gdy wątek znajduje się w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="7be6e-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="7be6e-113">Użyj [ICorDebugRegisterSet](icordebugregisterset-interface.md) dla wątków w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="7be6e-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="7be6e-114">Nie trzeba zmieniać kontekstu wątku podczas zdarzenia debugowania poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="7be6e-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="7be6e-115">Przesyłane dane muszą być strukturą kontekstu dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="7be6e-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="7be6e-116">Ta metoda może uszkodzić środowisko uruchomieniowe, jeśli jest używane nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="7be6e-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7be6e-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7be6e-117">Requirements</span></span>  
 <span data-ttu-id="7be6e-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7be6e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7be6e-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7be6e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7be6e-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7be6e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7be6e-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7be6e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
