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
ms.openlocfilehash: 632d3912bae28da22e701078bb47d2d8dbfd3644
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="f2610-102">ICorDebugRegisterSet::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="f2610-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="f2610-103">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="f2610-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2610-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2610-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2610-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2610-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="f2610-106">[in] Rozmiar w bajtach z `context` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f2610-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="f2610-107">[w, out] Tablicę bajtów, które tworzą Win32 `CONTEXT` strukturę dla bieżącej platformie.</span><span class="sxs-lookup"><span data-stu-id="f2610-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2610-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2610-108">Remarks</span></span>  
 <span data-ttu-id="f2610-109">Debuger powinien wywoływać tej funkcji, zamiast Win32 `GetThreadContext` działać, ponieważ wątek może być w stanie "hijacked", gdy kontekst zostało tymczasowo zmienione.</span><span class="sxs-lookup"><span data-stu-id="f2610-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="f2610-110">Zwrócone dane mają Win32 `CONTEXT` strukturę dla bieżącej platformie.</span><span class="sxs-lookup"><span data-stu-id="f2610-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="f2610-111">Ramek liścia klientów należy sprawdzić rejestrujący są prawidłowe, za pomocą [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="f2610-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2610-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2610-112">Requirements</span></span>  
 <span data-ttu-id="f2610-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2610-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2610-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2610-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2610-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2610-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2610-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2610-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2610-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2610-117">See Also</span></span>  
 [<span data-ttu-id="f2610-118">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2610-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="f2610-119">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2610-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
