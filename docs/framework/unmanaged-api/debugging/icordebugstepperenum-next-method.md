---
title: "ICorDebugStepperEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepperEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a0ad2e3361387875178e8261fad4159a3064da1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="3419f-102">ICorDebugStepperEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="3419f-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="3419f-103">Pobiera określoną liczbę wystąpień ICorDebugStepper — z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="3419f-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3419f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3419f-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3419f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3419f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3419f-106">[in] Liczba `ICorDebugStepper` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="3419f-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="3419f-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugStepper` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3419f-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3419f-108">[out] Wskaźnik do liczby `ICorDebugStepper` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="3419f-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="3419f-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="3419f-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3419f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3419f-110">Requirements</span></span>  
 <span data-ttu-id="3419f-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3419f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3419f-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3419f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3419f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3419f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3419f-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3419f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
