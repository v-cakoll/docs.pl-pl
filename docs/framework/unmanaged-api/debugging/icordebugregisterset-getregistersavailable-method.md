---
title: "ICorDebugRegisterSet::GetRegistersAvailable — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa4dd904b07aa2c9157e61e6968e96ef797ad3f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="0e378-102">ICorDebugRegisterSet::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="0e378-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="0e378-103">Pobiera bit maski wskazujący, który rejestruje w tym [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="0e378-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e378-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e378-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e378-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e378-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="0e378-106">[out] Maska bitowa, która wskazuje, który rejestruje są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="0e378-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e378-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e378-107">Remarks</span></span>  
 <span data-ttu-id="0e378-108">Rejestr może być niedostępna, jeśli nie można określić wartość dla danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="0e378-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="0e378-109">Zwrócony maska zawiera nieco dla poszczególnych rejestru (1 << indeks rejestru).</span><span class="sxs-lookup"><span data-stu-id="0e378-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="0e378-110">Wartość bitowa wynosi 1, jeśli rejestr jest dostępny, lub wartość 0, jeśli nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="0e378-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e378-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e378-111">Requirements</span></span>  
 <span data-ttu-id="0e378-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e378-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e378-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e378-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e378-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e378-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e378-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e378-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e378-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e378-116">See Also</span></span>  
 [<span data-ttu-id="0e378-117">ICorDebugRegisterSet — interfejs</span><span class="sxs-lookup"><span data-stu-id="0e378-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="0e378-118">ICorDebugRegisterSet2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="0e378-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
