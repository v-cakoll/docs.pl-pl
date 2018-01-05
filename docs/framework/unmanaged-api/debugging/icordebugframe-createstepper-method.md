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
ms.workload: dotnet
ms.openlocfilehash: 93f6741a030e72406fb8099c6373896d14cb9332
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="a87d8-102">ICorDebugFrame::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="a87d8-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="a87d8-103">Pobiera stepper, umożliwiający debugera do wykonywania operacji wykonywania krokowego względem tego ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="a87d8-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a87d8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a87d8-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a87d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a87d8-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="a87d8-106">[out] Wskaźnik do adres obiektu ICorDebugStepper — który umożliwia debugera do wykonywania operacji wykonywania krokowego względem bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="a87d8-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a87d8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a87d8-107">Remarks</span></span>  
 <span data-ttu-id="a87d8-108">Jeśli ramka nie jest aktywne, zwykle mają obiektu stepper powrócić do ramki, przed zakończeniem kroku.</span><span class="sxs-lookup"><span data-stu-id="a87d8-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a87d8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a87d8-109">Requirements</span></span>  
 <span data-ttu-id="a87d8-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a87d8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87d8-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a87d8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a87d8-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a87d8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a87d8-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a87d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
