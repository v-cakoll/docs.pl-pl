---
title: ICorDebugStepper::Deactivate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Deactivate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcd7bfb52cadf740d8fe3cb92a09b071f530b7ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417404"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="2c26a-102">ICorDebugStepper::Deactivate — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c26a-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="2c26a-103">Powoduje to ICorDebugStepper — anulować ostatnie polecenie krok, który otrzymał.</span><span class="sxs-lookup"><span data-stu-id="2c26a-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c26a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c26a-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2c26a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c26a-105">Remarks</span></span>  
 <span data-ttu-id="2c26a-106">Nowe polecenie wykonywania krokowego mogą być wystawiane po najbardziej ostatnio odebrano polecenie kroku zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="2c26a-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c26a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c26a-107">Requirements</span></span>  
 <span data-ttu-id="2c26a-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c26a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c26a-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c26a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c26a-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c26a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c26a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c26a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
