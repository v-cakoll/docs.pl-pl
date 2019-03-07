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
ms.openlocfilehash: c1ee576f41d20fdf4523fb4b566c3f2ce870d62c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469095"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="b0e3e-102">ICorDebugRegisterSet::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0e3e-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="b0e3e-103">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="b0e3e-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0e3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0e3e-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0e3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0e3e-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="b0e3e-106">[in] Rozmiar w bajtach z `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b0e3e-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="b0e3e-107">[out w] Tablica bajtów, które tworzą Win32 `CONTEXT` struktury dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="b0e3e-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0e3e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0e3e-108">Remarks</span></span>  
 <span data-ttu-id="b0e3e-109">Debuger powinien wywołać tę funkcję, zamiast Win32 `GetThreadContext` działać, ponieważ wątek może być w stanie "przejętego", gdzie kontekst zostało tymczasowo zmienione.</span><span class="sxs-lookup"><span data-stu-id="b0e3e-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="b0e3e-110">Dane zwracane to Win32 `CONTEXT` struktury dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="b0e3e-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="b0e3e-111">Dla ramek elementu członkowskiego typu liść klientów należy sprawdzić rejestrujący są prawidłowe, za pomocą [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="b0e3e-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0e3e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0e3e-112">Requirements</span></span>  
 <span data-ttu-id="b0e3e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e3e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e3e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0e3e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0e3e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0e3e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0e3e-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e3e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e3e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0e3e-117">See also</span></span>
- [<span data-ttu-id="b0e3e-118">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0e3e-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="b0e3e-119">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0e3e-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
