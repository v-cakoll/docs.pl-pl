---
title: ICorDebugStepper::SetUnmappedStopMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ff393b119c349e34898b781c3185cc82f2dba11f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137550"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="e8ee0-102">ICorDebugStepper::SetUnmappedStopMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8ee0-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="e8ee0-103">Ustawia wartość określającą typ niezamapowanego kodu, w którym wykonanie zostanie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="e8ee0-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ee0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8ee0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8ee0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8ee0-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="e8ee0-106">podczas Wartość wyliczenia CorDebugUnmappedStop —, która określa typ niezamapowanego kodu, w którym debuger zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="e8ee0-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="e8ee0-107">Wartość domyślna to STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="e8ee0-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="e8ee0-108">Wartość STOP_UNMANAGED jest prawidłowa tylko z debugowaniem międzyoperacyjnym.</span><span class="sxs-lookup"><span data-stu-id="e8ee0-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8ee0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8ee0-109">Remarks</span></span>  
 <span data-ttu-id="e8ee0-110">Gdy debuger odnajdzie kompilację just-in-Time (JIT), która nie ma odpowiedniego mapowania do języka pośredniego firmy Microsoft (MSIL), zatrzymuje wykonywanie, jeśli ustawiono flagę, która określa ten typ niezamapowanego kodu; w przeciwnym razie w dalszym ciągu kontynuuje działanie.</span><span class="sxs-lookup"><span data-stu-id="e8ee0-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="e8ee0-111">Jeśli debuger nie używa stepper do wprowadzania metody, nie będzie koniecznie przekroczyć niezamapowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e8ee0-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ee0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8ee0-112">Requirements</span></span>  
 <span data-ttu-id="e8ee0-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ee0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ee0-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e8ee0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8ee0-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e8ee0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8ee0-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ee0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
