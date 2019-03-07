---
title: ICorDebugFrame::CreateStepper — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fe3cbc4bad83496bcc58aaea60e6724b1d1f06c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466391"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="4bfe9-102">ICorDebugFrame::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="4bfe9-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="4bfe9-103">Pobiera stepper, umożliwiająca debugera do wykonywania operacji przechodzenia krok po kroku względem tego ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="4bfe9-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bfe9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bfe9-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bfe9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bfe9-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="4bfe9-106">[out] Wskaźnik na adres ICorDebugStepper — obiekt, który pozwala debugerowi na wykonywanie operacji przechodzenia krok po kroku względem bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="4bfe9-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bfe9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bfe9-107">Remarks</span></span>  
 <span data-ttu-id="4bfe9-108">Jeśli ramki nie jest aktywny, obiekt stepper zwykle musi powrócić do ramki, przed zakończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="4bfe9-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bfe9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bfe9-109">Requirements</span></span>  
 <span data-ttu-id="4bfe9-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bfe9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bfe9-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bfe9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bfe9-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bfe9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bfe9-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bfe9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
