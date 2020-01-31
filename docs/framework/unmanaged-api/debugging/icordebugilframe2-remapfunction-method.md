---
title: ICorDebugILFrame2::RemapFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
ms.openlocfilehash: f4f73b99b4cb48690a2a8611dbf5a5420adab5d4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794355"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="7aed0-102">ICorDebugILFrame2::RemapFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="7aed0-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="7aed0-103">Ponownie mapuje edytowaną funkcję poprzez określenie nowego przesunięcia języka pośredniego firmy Microsoft (MSIL)</span><span class="sxs-lookup"><span data-stu-id="7aed0-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aed0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7aed0-104">Syntax</span></span>  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aed0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7aed0-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="7aed0-106">podczas Nowe przesunięcie MSIL ramki stosu, w którym należy umieścić wskaźnik instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7aed0-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="7aed0-107">Ta wartość musi być punktem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7aed0-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="7aed0-108">Jest on odpowiedzialny za zagwarantowanie ważności tej wartości.</span><span class="sxs-lookup"><span data-stu-id="7aed0-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="7aed0-109">Na przykład przesunięcie MSIL jest nieprawidłowe, jeśli znajduje się poza granicami funkcji.</span><span class="sxs-lookup"><span data-stu-id="7aed0-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7aed0-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7aed0-110">Remarks</span></span>  
 <span data-ttu-id="7aed0-111">Po edytowaniu funkcji ramki debuger może wywołać metodę `RemapFunction`, aby dokonać zamiany w najnowszej wersji funkcji ramki, aby można ją było wykonać.</span><span class="sxs-lookup"><span data-stu-id="7aed0-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="7aed0-112">Wykonanie kodu rozpocznie się w danym przesunięciu MSIL.</span><span class="sxs-lookup"><span data-stu-id="7aed0-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7aed0-113">Wywoływanie `RemapFunction`, takich jak wywołanie [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md), natychmiast unieważnia wszystkie interfejsy debugowania, które są związane z generowaniem śladu stosu dla wątku.</span><span class="sxs-lookup"><span data-stu-id="7aed0-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="7aed0-114">Te interfejsy obejmują [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame i ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="7aed0-114">These interfaces include [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="7aed0-115">Metodę `RemapFunction` można wywołać tylko w kontekście bieżącej ramki i tylko w jednym z następujących przypadków:</span><span class="sxs-lookup"><span data-stu-id="7aed0-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="7aed0-116">Po odebraniu wywołania zwrotnego [ICorDebugManagedCallback2:: FunctionRemapOpportunity —](icordebugmanagedcallback2-functionremapopportunity-method.md) , które nie było jeszcze kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="7aed0-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="7aed0-117">Mimo że wykonywanie kodu zostało zatrzymane z powodu zdarzenia [ICorDebugManagedCallback:: EditAndContinueRemap —](icordebugmanagedcallback-editandcontinueremap-method.md) dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="7aed0-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aed0-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7aed0-118">Requirements</span></span>  
 <span data-ttu-id="7aed0-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aed0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aed0-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7aed0-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aed0-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7aed0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aed0-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aed0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
