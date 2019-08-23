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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95e8ad1ddce57252b7af3c7d72e8f8eb7bdb76b0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935092"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="1becb-102">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1becb-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="1becb-103">Rozszerza możliwości interfejsu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) dla platform sprzętowych, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="1becb-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1becb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1becb-104">Methods</span></span>  
  
|<span data-ttu-id="1becb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1becb-105">Method</span></span>|<span data-ttu-id="1becb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1becb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1becb-107">GetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="1becb-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="1becb-108">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.</span><span class="sxs-lookup"><span data-stu-id="1becb-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="1becb-109">GetRegistersAvailable, metoda</span><span class="sxs-lookup"><span data-stu-id="1becb-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="1becb-110">Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="1becb-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="1becb-111">SetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="1becb-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="1becb-112">Nie zaimplementowane w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="1becb-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1becb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1becb-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1becb-114">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="1becb-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1becb-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1becb-115">Requirements</span></span>  
 <span data-ttu-id="1becb-116">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1becb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1becb-117">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1becb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1becb-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1becb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1becb-119">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1becb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1becb-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1becb-120">See also</span></span>

- [<span data-ttu-id="1becb-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1becb-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1becb-122">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="1becb-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
