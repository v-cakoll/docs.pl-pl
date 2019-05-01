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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92885d2a6514839a864d6a345dd8af8b07b90c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946526"
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="853b2-102">ICorDebugILFrame2::RemapFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="853b2-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="853b2-103">Ponownie mapuje przeprowadzono edycję funkcji, określając nowy przesunięcia języka pośredniego (MSIL) firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="853b2-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="853b2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="853b2-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="853b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="853b2-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="853b2-106">[in] Ramka stosu wskaźnik instrukcji ma zostać umieszczony nowy przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="853b2-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="853b2-107">Ta wartość musi być punktu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="853b2-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="853b2-108">Odpowiada za wywołującego Sprawdź poprawność tej wartości.</span><span class="sxs-lookup"><span data-stu-id="853b2-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="853b2-109">Na przykład przesunięcie MSIL nie jest prawidłowy, jeśli znajduje się poza zakresem funkcji.</span><span class="sxs-lookup"><span data-stu-id="853b2-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="853b2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="853b2-110">Remarks</span></span>  
 <span data-ttu-id="853b2-111">Podczas edycji funkcji ramki debuger może wywołać `RemapFunction` metodę, aby zamienić w najnowszej wersji funkcji ramki, dzięki czemu mogą być wykonywane.</span><span class="sxs-lookup"><span data-stu-id="853b2-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="853b2-112">Wykonanie kodu spowoduje rozpoczęcie od danego przesunięcia MSIL.</span><span class="sxs-lookup"><span data-stu-id="853b2-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="853b2-113">Wywoływanie `RemapFunction`, tak jak podczas wywoływania [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), natychmiast spowoduje unieważnienie wszystkich interfejsów debugowania, które są związane z generowaniem ślad stosu dla wątku.</span><span class="sxs-lookup"><span data-stu-id="853b2-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="853b2-114">Te interfejsy zawierają [icordebugchain —](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, icordebuginternalframe — i icordebugnativeframe —.</span><span class="sxs-lookup"><span data-stu-id="853b2-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="853b2-115">`RemapFunction` Metoda może być wywoływana tylko w kontekście bieżącej ramki i tylko w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="853b2-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
- <span data-ttu-id="853b2-116">Po otrzymaniu [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) wywołanie zwrotne, które jeszcze nie jest kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="853b2-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
- <span data-ttu-id="853b2-117">Podczas wykonywania kodu została zatrzymana z powodu [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) zdarzenia dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="853b2-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="853b2-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="853b2-118">Requirements</span></span>  
 <span data-ttu-id="853b2-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="853b2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="853b2-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="853b2-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="853b2-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="853b2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="853b2-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="853b2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
