---
title: ICorDebugStepper::SetRangeIL — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: b3153a88867d249aad8365bb774348fb8c9d57d5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791753"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="1980f-102">ICorDebugStepper::SetRangeIL — Metoda</span><span class="sxs-lookup"><span data-stu-id="1980f-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="1980f-103">Ustawia wartość określającą, czy wywołania do [ICorDebugStepper:: StepRange —](icordebugstepper-steprange-method.md) przechodzą wartości argumentów, które są względne dla kodu natywnego lub względem kodu języka pośredniego firmy Microsoft (MSIL) metody, która jest testowana przez.</span><span class="sxs-lookup"><span data-stu-id="1980f-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1980f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1980f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1980f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1980f-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="1980f-106">podczas Ustaw na `true`, aby określić, że zakresy są względne dla kodu MSIL.</span><span class="sxs-lookup"><span data-stu-id="1980f-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="1980f-107">Ustaw na `false`, aby określić, że zakresy są względne dla kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="1980f-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="1980f-108">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="1980f-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1980f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1980f-109">Requirements</span></span>  
 <span data-ttu-id="1980f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1980f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1980f-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1980f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1980f-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1980f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1980f-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1980f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
