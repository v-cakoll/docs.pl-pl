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
ms.openlocfilehash: 9d8bd6ab13fa408fd7390aaeb76baee274742f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137704"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="5fc5b-102">ICorDebugRegisterSet::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="5fc5b-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="5fc5b-103">Pobiera maskę bitową wskazującą, które rejestry w tym [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="5fc5b-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fc5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fc5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5fc5b-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="5fc5b-106">określoną Maska bitów wskazująca, które rejestry są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="5fc5b-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fc5b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fc5b-107">Remarks</span></span>  
 <span data-ttu-id="5fc5b-108">Rejestr może być niedostępny, jeśli nie można ustalić jego wartości dla danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="5fc5b-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="5fc5b-109">Zwracana Maska zawiera bit dla każdej rejestracji (1 < < indeks rejestru).</span><span class="sxs-lookup"><span data-stu-id="5fc5b-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="5fc5b-110">Wartość bitowa to 1, jeśli rejestr jest dostępny, lub 0, jeśli nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="5fc5b-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fc5b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5fc5b-111">Requirements</span></span>  
 <span data-ttu-id="5fc5b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fc5b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fc5b-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5fc5b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fc5b-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5fc5b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fc5b-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fc5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fc5b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fc5b-116">See also</span></span>

- [<span data-ttu-id="5fc5b-117">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="5fc5b-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="5fc5b-118">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5fc5b-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
