---
title: "ICorDebugStepper::Deactivate — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Deactivate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Deactivate
helpviewer_keywords:
- Deactivate method [.NET Framework debugging]
- ICorDebugStepper::Deactivate method [.NET Framework debugging]
ms.assetid: 855f4199-b62d-40ce-998e-1eb4a1772142
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 056d60a56c37126163361166e16da5d7949e2dbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperdeactivate-method"></a><span data-ttu-id="faa15-102">ICorDebugStepper::Deactivate — Metoda</span><span class="sxs-lookup"><span data-stu-id="faa15-102">ICorDebugStepper::Deactivate Method</span></span>
<span data-ttu-id="faa15-103">Powoduje to ICorDebugStepper — anulować ostatnie polecenie krok, który otrzymał.</span><span class="sxs-lookup"><span data-stu-id="faa15-103">Causes this ICorDebugStepper to cancel the last step command that it received.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="faa15-104">Syntax</span></span>  
  
```  
HRESULT Deactivate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="faa15-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="faa15-105">Remarks</span></span>  
 <span data-ttu-id="faa15-106">Nowe polecenie wykonywania krokowego mogą być wystawiane po najbardziej ostatnio odebrano polecenie kroku zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="faa15-106">A new stepping command may be issued after the most recently received step command has been canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa15-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="faa15-107">Requirements</span></span>  
 <span data-ttu-id="faa15-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa15-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa15-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="faa15-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="faa15-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faa15-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faa15-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa15-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
