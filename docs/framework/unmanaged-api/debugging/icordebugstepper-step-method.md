---
title: ICorDebugStepper::Step — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2d282e27ec5068fa6fe7f58ba95458fdc219972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="28738-102">ICorDebugStepper::Step — Metoda</span><span class="sxs-lookup"><span data-stu-id="28738-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="28738-103">Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku oraz opcjonalnie można kontynuować krokowe funkcje, które są wywoływane w wątku pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="28738-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28738-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28738-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28738-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28738-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="28738-106">[in] Ustaw `true` do kroku do funkcji, która jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="28738-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="28738-107">Ustaw `false` do kroku przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="28738-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28738-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28738-108">Remarks</span></span>  
 <span data-ttu-id="28738-109">Krok działanie jest kończone po środowisko uruchomieniowe języka wspólnego wykonuje następną instrukcję zarządzanych w tym stepper ramki.</span><span class="sxs-lookup"><span data-stu-id="28738-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="28738-110">Jeśli `Step` jest wywoływana na stepper, która nie jest w kod zarządzany, kroku zostanie zakończony podczas następnej instrukcji kod zarządzany jest wykonywany przez wątek.</span><span class="sxs-lookup"><span data-stu-id="28738-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28738-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28738-111">Requirements</span></span>  
 <span data-ttu-id="28738-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28738-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28738-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28738-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28738-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28738-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28738-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28738-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
