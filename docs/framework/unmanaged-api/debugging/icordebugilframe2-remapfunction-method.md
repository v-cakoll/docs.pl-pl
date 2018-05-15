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
ms.openlocfilehash: 9f03d8c993be1ac83ca84275bcb94f1bb3cdf884
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="00626-102">ICorDebugILFrame2::RemapFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="00626-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="00626-103">Ponownie mapuje funkcję edytowany przez określenie nowego przesunięcie język pośredni (MSIL) firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="00626-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00626-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00626-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00626-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00626-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="00626-106">[in] Ramka stosu wskaźnik instrukcji ma zostać umieszczony nowy przesunięcie MSIL.</span><span class="sxs-lookup"><span data-stu-id="00626-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="00626-107">Ta wartość musi być punktu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="00626-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="00626-108">Odpowiada wywołującego Sprawdź poprawność tej wartości.</span><span class="sxs-lookup"><span data-stu-id="00626-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="00626-109">Na przykład przesunięcie MSIL nie jest prawidłowy, jeśli znajduje się poza zakresem funkcji.</span><span class="sxs-lookup"><span data-stu-id="00626-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00626-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00626-110">Remarks</span></span>  
 <span data-ttu-id="00626-111">Podczas edycji funkcja ramki debuger może wywołać `RemapFunction` sposób wymiany w ostatniej wersji funkcja ramki, tak aby można było wykonać.</span><span class="sxs-lookup"><span data-stu-id="00626-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="00626-112">Wykonywanie kodu zostanie rozpoczęte od danego przesunięcia MSIL.</span><span class="sxs-lookup"><span data-stu-id="00626-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00626-113">Wywoływanie `RemapFunction`, takiej jak wywołanie [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), natychmiast spowoduje unieważnienie wszystkich interfejsów debugowania, które nie są związane z generowaniem ślad stosu wątku.</span><span class="sxs-lookup"><span data-stu-id="00626-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="00626-114">Te interfejsy zawierają [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame i ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="00626-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="00626-115">`RemapFunction` Metodę można wywołać tylko w kontekście bieżącej ramki i tylko w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="00626-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
-   <span data-ttu-id="00626-116">Po otrzymaniu [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) wywołania zwrotnego, która nie ma jeszcze kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="00626-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
-   <span data-ttu-id="00626-117">Podczas wykonywania kodu została zatrzymana z powodu [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) zdarzeń dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="00626-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00626-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00626-118">Requirements</span></span>  
 <span data-ttu-id="00626-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00626-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00626-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00626-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00626-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00626-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00626-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00626-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
