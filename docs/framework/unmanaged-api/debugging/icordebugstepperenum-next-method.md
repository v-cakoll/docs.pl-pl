---
title: ICorDebugStepperEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: 293d1a9cd93b5ce45105427e7df864ad8bfbe77a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379195"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="5e4a3-102">ICorDebugStepperEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e4a3-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="5e4a3-103">Pobiera określoną liczbę wystąpień ICorDebugStepper z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="5e4a3-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e4a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e4a3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e4a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e4a3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5e4a3-106">podczas Liczba `ICorDebugStepper` wystąpień do pobrania.</span><span class="sxs-lookup"><span data-stu-id="5e4a3-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="5e4a3-107">określoną Tablica wskaźników, z których każdy wskazuje `ICorDebugStepper` obiekt.</span><span class="sxs-lookup"><span data-stu-id="5e4a3-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5e4a3-108">określoną Wskaźnik do liczby `ICorDebugStepper` faktycznie zwróconych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="5e4a3-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="5e4a3-109">Ta wartość może być równa null, jeśli `celt` jest taka.</span><span class="sxs-lookup"><span data-stu-id="5e4a3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e4a3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e4a3-110">Requirements</span></span>  
 <span data-ttu-id="5e4a3-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e4a3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e4a3-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5e4a3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e4a3-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5e4a3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e4a3-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e4a3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
