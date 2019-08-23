---
title: ICorDebugRegisterSet — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6419a525a8a542295751defb97e67a83220730b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965063"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="2eacb-102">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2eacb-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="2eacb-103">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="2eacb-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2eacb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2eacb-104">Methods</span></span>  
  
|<span data-ttu-id="2eacb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2eacb-105">Method</span></span>|<span data-ttu-id="2eacb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2eacb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2eacb-107">GetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="2eacb-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="2eacb-108">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.</span><span class="sxs-lookup"><span data-stu-id="2eacb-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="2eacb-109">GetRegistersAvailable, metoda</span><span class="sxs-lookup"><span data-stu-id="2eacb-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="2eacb-110">Pobiera maskę bitową wskazującą, które rejestry w tej `ICorDebugRegisterSet` chwili są dostępne.</span><span class="sxs-lookup"><span data-stu-id="2eacb-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="2eacb-111">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="2eacb-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="2eacb-112">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="2eacb-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="2eacb-113">SetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="2eacb-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="2eacb-114">Nie zaimplementowane dla .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="2eacb-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="2eacb-115">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="2eacb-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="2eacb-116">Nie zaimplementowane dla .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="2eacb-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eacb-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2eacb-117">Remarks</span></span>  
 <span data-ttu-id="2eacb-118">`ICorDebugRegisterSet` Interfejs obsługuje tylko rejestry 32-bitowe.</span><span class="sxs-lookup"><span data-stu-id="2eacb-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="2eacb-119">Użyj interfejsu [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) na platformach, takich jak IA-64, które wymagają dodatkowych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="2eacb-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eacb-120">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2eacb-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eacb-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2eacb-121">Requirements</span></span>  
 <span data-ttu-id="2eacb-122">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eacb-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eacb-123">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2eacb-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2eacb-124">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2eacb-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eacb-125">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eacb-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eacb-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eacb-126">See also</span></span>

- [<span data-ttu-id="2eacb-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2eacb-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2eacb-128">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2eacb-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
