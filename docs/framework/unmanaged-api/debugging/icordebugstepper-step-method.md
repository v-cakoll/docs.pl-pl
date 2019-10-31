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
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137535"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="c46fe-102">ICorDebugStepper::Step — Metoda</span><span class="sxs-lookup"><span data-stu-id="c46fe-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="c46fe-103">Powoduje, że ICorDebugStepper to jeden krok za pomocą zawartego w nim wątku i opcjonalnie, aby kontynuować wykonywanie jednostopniowe za pomocą funkcji, które są wywoływane w wątku.</span><span class="sxs-lookup"><span data-stu-id="c46fe-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c46fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c46fe-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c46fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c46fe-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="c46fe-106">podczas Ustaw, aby `true` wkroczyć do funkcji, która jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="c46fe-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="c46fe-107">Ustaw na `false`, aby przekroczyć funkcję.</span><span class="sxs-lookup"><span data-stu-id="c46fe-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c46fe-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c46fe-108">Remarks</span></span>  
 <span data-ttu-id="c46fe-109">Krok zostaje zakończony, gdy środowisko uruchomieniowe języka wspólnego wykonuje następną zarządzaną instrukcję w tej stepper.</span><span class="sxs-lookup"><span data-stu-id="c46fe-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="c46fe-110">Jeśli `Step` jest wywoływana w stepper, która nie jest w kodzie zarządzanym, krok zostanie ukończony po wykonaniu kolejnej instrukcji kodu zarządzanego przez wątek.</span><span class="sxs-lookup"><span data-stu-id="c46fe-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c46fe-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c46fe-111">Requirements</span></span>  
 <span data-ttu-id="c46fe-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c46fe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c46fe-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c46fe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c46fe-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c46fe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c46fe-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c46fe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
