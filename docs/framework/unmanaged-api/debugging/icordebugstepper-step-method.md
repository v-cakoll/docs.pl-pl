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
ms.openlocfilehash: 39d2fd0163b0e61295187461d5dbdf5742450306
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379516"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="ca73c-102">ICorDebugStepper::Step — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca73c-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="ca73c-103">Powoduje, że ICorDebugStepper to jeden krok za pomocą zawartego w nim wątku i opcjonalnie, aby kontynuować wykonywanie jednostopniowe za pomocą funkcji, które są wywoływane w wątku.</span><span class="sxs-lookup"><span data-stu-id="ca73c-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca73c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca73c-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca73c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca73c-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="ca73c-106">podczas Ustaw, aby `true` wkroczyć do funkcji, która jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="ca73c-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="ca73c-107">Ustaw, aby przekroczyć `false` funkcję.</span><span class="sxs-lookup"><span data-stu-id="ca73c-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca73c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca73c-108">Remarks</span></span>  
 <span data-ttu-id="ca73c-109">Krok zostaje zakończony, gdy środowisko uruchomieniowe języka wspólnego wykonuje następną zarządzaną instrukcję w tej stepper.</span><span class="sxs-lookup"><span data-stu-id="ca73c-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="ca73c-110">Jeśli `Step` jest wywoływana na stepper, który nie jest w kodzie zarządzanym, krok zostanie ukończony, gdy Następna instrukcja kodu zarządzanego zostanie wykonana przez wątek.</span><span class="sxs-lookup"><span data-stu-id="ca73c-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca73c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca73c-111">Requirements</span></span>  
 <span data-ttu-id="ca73c-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca73c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca73c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ca73c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca73c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ca73c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca73c-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca73c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
