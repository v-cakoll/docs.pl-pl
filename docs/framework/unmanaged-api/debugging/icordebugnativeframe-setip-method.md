---
title: "ICorDebugNativeFrame::SetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 563566a877d589ecd32575c095cdc812c28f6334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="c4925-102">ICorDebugNativeFrame::SetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="c4925-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="c4925-103">Ustawia wskaźnik instrukcji w określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="c4925-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4925-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4925-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4925-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4925-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="c4925-106">[in] Przesunięcie lokalizacji w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="c4925-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4925-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4925-107">Remarks</span></span>  
 <span data-ttu-id="c4925-108">Wywołuje się `SetIP` natychmiast unieważnia wszystkie ramki i łańcuchów bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="c4925-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="c4925-109">Jeśli debuger musi ramki informacji po wywołaniu `SetIP`, należy wykonać nowe ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="c4925-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="c4925-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) będzie próbował zachować ramki stosu w prawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="c4925-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="c4925-111">Jednak nawet jeśli ramki jest w nieprawidłowym stanie, ile dotyczy to środowisko uruchomieniowe, nadal mogą istnieć problemy, takie jak niezainicjowanych zmiennych lokalnych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c4925-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="c4925-112">Element wywołujący jest odpowiedzialny za spójność uruchomiony program.</span><span class="sxs-lookup"><span data-stu-id="c4925-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="c4925-113">Na platformach 64-bitowych wskaźnik instrukcji nie można przenieść poza `catch` lub `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="c4925-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="c4925-114">Jeśli `SetIP` jest nazywany aby ruch na 64-bitowej platformy, zwróci HRESULT informujący o niepowodzeniu.</span><span class="sxs-lookup"><span data-stu-id="c4925-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4925-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4925-115">Requirements</span></span>  
 <span data-ttu-id="c4925-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4925-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4925-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4925-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4925-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4925-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4925-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4925-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4925-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4925-120">See Also</span></span>  
 
