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
ms.openlocfilehash: 444390622ca68244661b91dc85814b05556b12a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994321"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="3306b-102">ICorDebugStepper::Step — Metoda</span><span class="sxs-lookup"><span data-stu-id="3306b-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="3306b-103">Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku i, opcjonalnie, aby kontynuować, krokowe funkcje, które są wywoływane w wątku pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="3306b-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3306b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3306b-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3306b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3306b-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="3306b-106">[in] Ustaw `true` aby wejść do funkcji, która jest wywołana w wątku.</span><span class="sxs-lookup"><span data-stu-id="3306b-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="3306b-107">Ustaw `false` do kroku za pośrednictwem funkcji.</span><span class="sxs-lookup"><span data-stu-id="3306b-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3306b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3306b-108">Remarks</span></span>  
 <span data-ttu-id="3306b-109">Ten krok zostanie ukończone, gdy środowisko uruchomieniowe języka wspólnego wykonuje następnej instrukcji zarządzanych w ramce tego stepper.</span><span class="sxs-lookup"><span data-stu-id="3306b-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="3306b-110">Jeśli `Step` jest wywoływana na stepper, który nie jest w kodu zarządzanego, ten krok zostanie ukończone, gdy następnej instrukcji kodu zarządzanego jest wykonywana przez wątek.</span><span class="sxs-lookup"><span data-stu-id="3306b-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3306b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3306b-111">Requirements</span></span>  
 <span data-ttu-id="3306b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3306b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3306b-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3306b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3306b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3306b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3306b-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3306b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
