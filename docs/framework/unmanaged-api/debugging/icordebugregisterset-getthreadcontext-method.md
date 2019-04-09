---
title: ICorDebugRegisterSet::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fecbcff0fd124b94aeeecf82e23d9875c34ebb9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091580"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="76b9c-102">ICorDebugRegisterSet::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="76b9c-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="76b9c-103">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="76b9c-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76b9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76b9c-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76b9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76b9c-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="76b9c-106">[in] Rozmiar w bajtach z `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="76b9c-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="76b9c-107">[out w] Tablica bajtów, które tworzą Win32 `CONTEXT` struktury dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="76b9c-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76b9c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76b9c-108">Remarks</span></span>  
 <span data-ttu-id="76b9c-109">Debuger powinien wywołać tę funkcję, zamiast Win32 `GetThreadContext` działać, ponieważ wątek może być w stanie "przejętego", gdzie kontekst zostało tymczasowo zmienione.</span><span class="sxs-lookup"><span data-stu-id="76b9c-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="76b9c-110">Dane zwracane to Win32 `CONTEXT` struktury dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="76b9c-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="76b9c-111">Dla ramek elementu członkowskiego typu liść klientów należy sprawdzić rejestrujący są prawidłowe, za pomocą [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="76b9c-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76b9c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76b9c-112">Requirements</span></span>  
 <span data-ttu-id="76b9c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76b9c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76b9c-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76b9c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76b9c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76b9c-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="76b9c-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="76b9c-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="76b9c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76b9c-117">See also</span></span>

- [<span data-ttu-id="76b9c-118">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76b9c-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="76b9c-119">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76b9c-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
