---
title: "ICorDebugStepper::Step — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Step
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 914773adefd2ed4c1aa98310fd27a0cbc829bf49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="53add-102">ICorDebugStepper::Step — Metoda</span><span class="sxs-lookup"><span data-stu-id="53add-102">ICorDebugStepper::Step Method</span></span>
<span data-ttu-id="53add-103">Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku oraz opcjonalnie można kontynuować krokowe funkcje, które są wywoływane w wątku pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="53add-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53add-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53add-104">Syntax</span></span>  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53add-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53add-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="53add-106">[in] Ustaw `true` do kroku do funkcji, która jest wywoływana w wątku.</span><span class="sxs-lookup"><span data-stu-id="53add-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="53add-107">Ustaw `false` do kroku przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="53add-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53add-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53add-108">Remarks</span></span>  
 <span data-ttu-id="53add-109">Krok działanie jest kończone po środowisko uruchomieniowe języka wspólnego wykonuje następną instrukcję zarządzanych w tym stepper ramki.</span><span class="sxs-lookup"><span data-stu-id="53add-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="53add-110">Jeśli `Step` jest wywoływana na stepper, która nie jest w kod zarządzany, kroku zostanie zakończony podczas następnej instrukcji kod zarządzany jest wykonywany przez wątek.</span><span class="sxs-lookup"><span data-stu-id="53add-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53add-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53add-111">Requirements</span></span>  
 <span data-ttu-id="53add-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53add-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53add-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53add-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53add-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53add-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53add-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53add-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
