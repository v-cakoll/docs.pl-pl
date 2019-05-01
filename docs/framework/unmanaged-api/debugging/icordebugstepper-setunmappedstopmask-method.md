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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da799b0d4f4e5e4b281445baa35d95f992ba0b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987457"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="02f12-102">ICorDebugStepper::SetUnmappedStopMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="02f12-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="02f12-103">Ustawia wartość, która określa typ niezamapowane kodu, w którym wykonywanie zostanie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="02f12-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02f12-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02f12-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02f12-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="02f12-106">[in] Wartość cordebugunmappedstop — wyliczenie, który określa typ niezamapowane kodu, w której debuger będzie zatrzymuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="02f12-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="02f12-107">Wartość domyślna to STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="02f12-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="02f12-108">Wartość STOP_UNMANAGED tylko jest prawidłowa w przypadku debugowania międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="02f12-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02f12-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02f12-109">Remarks</span></span>  
 <span data-ttu-id="02f12-110">Gdy debuger wykryje just-in-time kompilacji (JIT), który nie ma odpowiedniego mapowania do języka Microsoft intermediate language (MSIL), zatrzymuje wykonywanie, jeśli została ustawiona flaga określania typu niezamapowane kodu; w przeciwnym razie wykonywanie krokowe w sposób niewidoczny dla użytkownika jest kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="02f12-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="02f12-111">Jeśli debuger nie używa stepper wprowadzenie metody, następnie go nie zawsze Przekrocz nad niezamapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="02f12-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f12-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02f12-112">Requirements</span></span>  
 <span data-ttu-id="02f12-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02f12-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f12-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02f12-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02f12-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02f12-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02f12-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f12-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
