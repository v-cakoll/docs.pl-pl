---
title: "ICorDebugStepper::StepOut — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d6462f166e9c734dacc7ebee13cb82e3b12158b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="ca88a-102">ICorDebugStepper::StepOut — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca88a-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="ca88a-103">Powoduje to ICorDebugStepper — aby pojedynczy krok za pomocą jego zawierającego wątku i do wykonania podczas bieżącej ramki zwraca sterowania do wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="ca88a-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca88a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca88a-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ca88a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca88a-105">Remarks</span></span>  
 <span data-ttu-id="ca88a-106">A `StepOut` operacja zostanie wykonana po powrocie zwykle z bieżącej ramki do wywoływania ramki.</span><span class="sxs-lookup"><span data-stu-id="ca88a-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="ca88a-107">Jeśli `StepOut` jest wywoływane, gdy za pomocą kodu niezarządzanego kroku ukończy po powrocie z do zarządzanego kodu, który wywołuje ona bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="ca88a-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="ca88a-108">W programie .NET Framework w wersji 2.0, nie używaj `StepOut` z STOP_UNMANAGED Flaga ponieważ zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ca88a-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="ca88a-109">(Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) można ustawić flagi wykonywanie krok po kroku.) Międzyoperacyjne debugery musi Wyjdź do kodu natywnego samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="ca88a-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca88a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca88a-110">Requirements</span></span>  
 <span data-ttu-id="ca88a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca88a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca88a-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca88a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca88a-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca88a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca88a-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca88a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
