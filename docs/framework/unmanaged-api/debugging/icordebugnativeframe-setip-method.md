---
title: ICorDebugNativeFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33a4315d8908906e9ae1511aa9501969752d4af6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484867"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="2faa8-102">ICorDebugNativeFrame::SetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="2faa8-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="2faa8-103">Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="2faa8-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2faa8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2faa8-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2faa8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2faa8-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="2faa8-106">[in] Przesunięcie lokalizacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="2faa8-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2faa8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2faa8-107">Remarks</span></span>  
 <span data-ttu-id="2faa8-108">Wywołania `SetIP` natychmiast unieważnia wszystkie ramki i łańcuchów dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="2faa8-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="2faa8-109">Jeśli debuger potrzebuje informacji o ramce po wywołaniu `SetIP`, należy wykonać, nowe ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="2faa8-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="2faa8-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) będzie próbował zachować ramki stosu w prawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="2faa8-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="2faa8-111">Jednak nawet jeśli ramki jest w nieprawidłowym stanie chodzi środowiska uruchomieniowego jest, nadal może być problemy, takie jak niezainicjowanych zmiennych lokalnych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="2faa8-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="2faa8-112">Obiekt wywołujący jest odpowiedzialny za spójność uruchomionego programu.</span><span class="sxs-lookup"><span data-stu-id="2faa8-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="2faa8-113">Na platformach 64-bitowy wskaźnik instrukcji nie można przenieść poza `catch` lub `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="2faa8-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="2faa8-114">Jeśli `SetIP` nazywa się przejście na platformie 64-bitowej, zwróci wartość HRESULT wskazujący awarię.</span><span class="sxs-lookup"><span data-stu-id="2faa8-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2faa8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2faa8-115">Requirements</span></span>  
 <span data-ttu-id="2faa8-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2faa8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2faa8-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2faa8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2faa8-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2faa8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2faa8-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2faa8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2faa8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2faa8-120">See also</span></span>

