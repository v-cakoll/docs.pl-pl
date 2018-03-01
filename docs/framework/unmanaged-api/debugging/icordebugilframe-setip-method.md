---
title: "ICorDebugILFrame::SetIP — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="36756-102">ICorDebugILFrame::SetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="36756-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="36756-103">Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="36756-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36756-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36756-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36756-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36756-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="36756-106">Przesunięcie lokalizacji w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="36756-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36756-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36756-107">Remarks</span></span>  
 <span data-ttu-id="36756-108">Wywołuje się `SetIP` natychmiast unieważnia wszystkie ramki i łańcuchów bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="36756-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="36756-109">Jeśli debuger musi ramki informacji po wywołaniu `SetIP`, należy wykonać nowe ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="36756-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="36756-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) będzie próbował zachować ramki stosu w prawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="36756-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="36756-111">Jednak nawet jeśli ramki jest w nieprawidłowym stanie, nadal mogą istnieć problemów, takich jak niezainicjowanych zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="36756-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="36756-112">Element wywołujący jest odpowiedzialny za zapewnienie spójności uruchomiony program.</span><span class="sxs-lookup"><span data-stu-id="36756-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="36756-113">Na platformach 64-bitowych wskaźnik instrukcji nie można przenieść poza `catch` lub `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="36756-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="36756-114">Jeśli `SetIP` jest nazywany aby ruch na 64-bitowej platformy, zwróci HRESULT informujący o niepowodzeniu.</span><span class="sxs-lookup"><span data-stu-id="36756-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36756-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36756-115">Requirements</span></span>  
 <span data-ttu-id="36756-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36756-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36756-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36756-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36756-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36756-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36756-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36756-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
