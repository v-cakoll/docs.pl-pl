---
title: ICorDebugRegisterSet2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: f989f1c1f29c63af54ff125f4ad1aaa2bcee6757
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378197"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="215e5-102">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="215e5-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="215e5-103">Rozszerza możliwości interfejsu [ICorDebugRegisterSet](icordebugregisterset-interface.md) dla platform sprzętowych, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="215e5-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="215e5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="215e5-104">Methods</span></span>  
  
|<span data-ttu-id="215e5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="215e5-105">Method</span></span>|<span data-ttu-id="215e5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="215e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="215e5-107">GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="215e5-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="215e5-108">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.</span><span class="sxs-lookup"><span data-stu-id="215e5-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="215e5-109">GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="215e5-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="215e5-110">Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="215e5-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="215e5-111">SetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="215e5-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="215e5-112">Nie zaimplementowane w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="215e5-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="215e5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="215e5-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="215e5-114">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="215e5-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="215e5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="215e5-115">Requirements</span></span>  
 <span data-ttu-id="215e5-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="215e5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="215e5-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="215e5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="215e5-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="215e5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="215e5-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="215e5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215e5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="215e5-120">See also</span></span>

- [<span data-ttu-id="215e5-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="215e5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="215e5-122">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="215e5-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
