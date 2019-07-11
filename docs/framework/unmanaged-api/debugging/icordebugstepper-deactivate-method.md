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
ms.openlocfilehash: b577e915422814fbd0060fdda53b9e2bf7cd091a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760724"
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="36537-102">ICorDebugStepper::Deactivate — Metoda</span><span class="sxs-lookup"><span data-stu-id="36537-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="36537-103">Powoduje to ICorDebugStepper — ostatnie polecenie kroku, który otrzymał anulowania.</span><span class="sxs-lookup"><span data-stu-id="36537-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36537-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36537-104">Syntax</span></span>  
  
```cpp  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="36537-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36537-105">Remarks</span></span>  
 <span data-ttu-id="36537-106">Mogą być wydawane nowego polecenia przechodzenia krok po kroku, po najbardziej niedawno odebrano polecenie kroku zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="36537-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36537-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36537-107">Requirements</span></span>  
 <span data-ttu-id="36537-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36537-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36537-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36537-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36537-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36537-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36537-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36537-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
