---
title: ICorDebugILFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af3f58fa7714b3c2b0ba387b1da650f0638dd6c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758776"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="97404-102">ICorDebugILFrame::SetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="97404-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="97404-103">Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie języka intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="97404-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97404-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97404-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97404-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97404-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="97404-106">Przesunięcie lokalizacji w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="97404-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97404-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97404-107">Remarks</span></span>  
 <span data-ttu-id="97404-108">Wywołania `SetIP` natychmiast unieważnia wszystkie ramki i łańcuchów dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="97404-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="97404-109">Jeśli debuger potrzebuje informacji o ramce po wywołaniu `SetIP`, należy wykonać, nowe ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="97404-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="97404-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) będzie próbował zachować ramki stosu w prawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="97404-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="97404-111">Jednak nawet jeśli ramki jest w nieprawidłowym stanie, nadal może istnieć problemy, takie jak niezainicjowanych zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="97404-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="97404-112">Obiekt wywołujący jest odpowiedzialny za zapewnienie spójności uruchomionego programu.</span><span class="sxs-lookup"><span data-stu-id="97404-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="97404-113">Na platformach 64-bitowy wskaźnik instrukcji nie można przenieść poza `catch` lub `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="97404-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="97404-114">Jeśli `SetIP` nazywa się przejście na platformie 64-bitowej, zwróci wartość HRESULT wskazujący awarię.</span><span class="sxs-lookup"><span data-stu-id="97404-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97404-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97404-115">Requirements</span></span>  
 <span data-ttu-id="97404-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97404-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97404-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97404-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97404-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97404-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97404-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97404-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
