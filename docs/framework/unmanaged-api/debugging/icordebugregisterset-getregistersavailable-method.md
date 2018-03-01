---
title: "ICorDebugRegisterSet::GetRegistersAvailable — Metoda"
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
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd7ff2b711d81ba1fe8fda9422587ec265dd88dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="f4ce6-102">ICorDebugRegisterSet::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="f4ce6-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="f4ce6-103">Pobiera bit maski wskazujący, który rejestruje w tym [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ce6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4ce6-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4ce6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4ce6-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="f4ce6-106">[out] Maska bitowa, która wskazuje, który rejestruje są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4ce6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4ce6-107">Remarks</span></span>  
 <span data-ttu-id="f4ce6-108">Rejestr może być niedostępna, jeśli nie można określić wartość dla danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="f4ce6-109">Zwrócony maska zawiera nieco dla poszczególnych rejestru (1 << indeks rejestru).</span><span class="sxs-lookup"><span data-stu-id="f4ce6-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="f4ce6-110">Wartość bitowa wynosi 1, jeśli rejestr jest dostępny, lub wartość 0, jeśli nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="f4ce6-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4ce6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4ce6-111">Requirements</span></span>  
 <span data-ttu-id="f4ce6-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4ce6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4ce6-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4ce6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4ce6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4ce6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4ce6-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4ce6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ce6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4ce6-116">See Also</span></span>  
 [<span data-ttu-id="f4ce6-117">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4ce6-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="f4ce6-118">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f4ce6-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
