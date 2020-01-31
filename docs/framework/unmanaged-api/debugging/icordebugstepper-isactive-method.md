---
title: ICorDebugStepper::IsActive — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791772"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="54b5a-102">ICorDebugStepper::IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="54b5a-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="54b5a-103">Pobiera wartość wskazującą, czy ten ICorDebugStepper aktualnie wykonuje krok.</span><span class="sxs-lookup"><span data-stu-id="54b5a-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54b5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54b5a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54b5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54b5a-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="54b5a-106">określoną Zwraca `true`, jeśli stepper aktualnie wykonuje krok; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="54b5a-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54b5a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54b5a-107">Remarks</span></span>  
 <span data-ttu-id="54b5a-108">Każda akcja krok pozostaje aktywna, dopóki debuger nie otrzyma wywołania [ICorDebugManagedCallback:: StepComplete —](icordebugmanagedcallback-stepcomplete-method.md) , które automatycznie dezaktywuje stepper.</span><span class="sxs-lookup"><span data-stu-id="54b5a-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="54b5a-109">Stepper może również zostać zdezaktywowany przedwcześnie przez wywołanie [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) przed osiągnięciem warunku wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="54b5a-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54b5a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54b5a-110">Requirements</span></span>  
 <span data-ttu-id="54b5a-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54b5a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54b5a-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54b5a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54b5a-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="54b5a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54b5a-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54b5a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
