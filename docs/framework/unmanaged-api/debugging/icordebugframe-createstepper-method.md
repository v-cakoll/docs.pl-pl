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
ms.openlocfilehash: 6ea2b24d37f56a5cb9e6b3dea0d666c8acc719dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091030"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="2440b-102">ICorDebugFrame::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="2440b-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="2440b-103">Pobiera stepper, który umożliwia debugerowi wykonywanie operacji krokowych względem tego ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="2440b-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2440b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2440b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2440b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2440b-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="2440b-106">określoną Wskaźnik do adresu obiektu ICorDebugStepper, który umożliwia debugerowi wykonywanie operacji krokowe względem bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="2440b-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2440b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2440b-107">Remarks</span></span>  
 <span data-ttu-id="2440b-108">Jeśli ramka nie jest aktywna, obiekt stepper zazwyczaj będzie musiał powrócić do ramki przed ukończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="2440b-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2440b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2440b-109">Requirements</span></span>  
 <span data-ttu-id="2440b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2440b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2440b-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2440b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2440b-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2440b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2440b-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2440b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
