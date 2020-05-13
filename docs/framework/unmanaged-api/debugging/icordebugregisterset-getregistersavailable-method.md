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
ms.openlocfilehash: 74eef0c1ec456d647e5a58e5009d2c77e5002289
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378292"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="c41e8-102">ICorDebugRegisterSet::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="c41e8-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="c41e8-103">Pobiera maskę bitową wskazującą, które rejestry w tym [ICorDebugRegisterSet](icordebugregisterset-interface.md) są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="c41e8-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c41e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c41e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c41e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c41e8-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="c41e8-106">określoną Maska bitów wskazująca, które rejestry są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="c41e8-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c41e8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c41e8-107">Remarks</span></span>  
 <span data-ttu-id="c41e8-108">Rejestr może być niedostępny, jeśli nie można ustalić jego wartości dla danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="c41e8-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="c41e8-109">Zwracana Maska zawiera bit dla każdej rejestracji (1 << indeksem rejestru).</span><span class="sxs-lookup"><span data-stu-id="c41e8-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="c41e8-110">Wartość bitowa to 1, jeśli rejestr jest dostępny, lub 0, jeśli nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="c41e8-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c41e8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c41e8-111">Requirements</span></span>  
 <span data-ttu-id="c41e8-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c41e8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c41e8-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c41e8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c41e8-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c41e8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c41e8-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c41e8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41e8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c41e8-116">See also</span></span>

- [<span data-ttu-id="c41e8-117">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c41e8-117">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="c41e8-118">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c41e8-118">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
