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
ms.openlocfilehash: 39b4e7e5123447a36254b55b6168c80e48c8dcab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205448"
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="2a072-102">ICorDebugFrame::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a072-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="2a072-103">Pobiera stepper, który umożliwia debugerowi wykonywanie operacji krokowych względem tego ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="2a072-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a072-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a072-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a072-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a072-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="2a072-106">określoną Wskaźnik do adresu obiektu ICorDebugStepper, który umożliwia debugerowi wykonywanie operacji krokowe względem bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="2a072-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a072-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a072-107">Remarks</span></span>  
 <span data-ttu-id="2a072-108">Jeśli ramka nie jest aktywna, obiekt stepper zazwyczaj będzie musiał powrócić do ramki przed ukończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="2a072-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a072-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a072-109">Requirements</span></span>  
 <span data-ttu-id="2a072-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a072-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a072-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2a072-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a072-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2a072-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a072-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a072-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
