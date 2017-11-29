---
title: "ICorDebugFrame::CreateStepper — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6f575febc488d01700c32198d4c00916dd5e249
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="5fb89-102">ICorDebugFrame::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="5fb89-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="5fb89-103">Pobiera stepper, umożliwiający debugera do wykonywania operacji wykonywania krokowego względem tego ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="5fb89-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fb89-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fb89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fb89-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="5fb89-106">[out] Wskaźnik do adres obiektu ICorDebugStepper — który umożliwia debugera do wykonywania operacji wykonywania krokowego względem bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="5fb89-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fb89-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fb89-107">Remarks</span></span>  
 <span data-ttu-id="5fb89-108">Jeśli ramka nie jest aktywne, zwykle mają obiektu stepper powrócić do ramki, przed zakończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="5fb89-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fb89-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fb89-109">Requirements</span></span>  
 <span data-ttu-id="5fb89-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fb89-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fb89-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fb89-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fb89-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fb89-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fb89-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fb89-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
