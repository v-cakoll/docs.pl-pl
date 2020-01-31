---
title: ICorDebugRegisterSet::GetRegistersAvailable — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: b137b956e06a2b2954918e4024860f9b234e7583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792107"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="93818-102">ICorDebugRegisterSet::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="93818-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="93818-103">Pobiera maskę bitową wskazującą, które rejestry w tym [ICorDebugRegisterSet](icordebugregisterset-interface.md) są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="93818-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93818-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93818-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93818-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93818-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="93818-106">określoną Maska bitów wskazująca, które rejestry są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="93818-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93818-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93818-107">Remarks</span></span>  
 <span data-ttu-id="93818-108">Rejestr może być niedostępny, jeśli nie można ustalić jego wartości dla danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="93818-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="93818-109">Zwracana Maska zawiera bit dla każdej rejestracji (1 < < indeks rejestru).</span><span class="sxs-lookup"><span data-stu-id="93818-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="93818-110">Wartość bitowa to 1, jeśli rejestr jest dostępny, lub 0, jeśli nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="93818-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93818-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93818-111">Requirements</span></span>  
 <span data-ttu-id="93818-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93818-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93818-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93818-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93818-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93818-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93818-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93818-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93818-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93818-116">See also</span></span>

- [<span data-ttu-id="93818-117">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="93818-117">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="93818-118">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="93818-118">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
