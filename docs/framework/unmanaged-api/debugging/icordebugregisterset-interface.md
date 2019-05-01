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
ms.openlocfilehash: 7b0a5d80d984a3c696b178c4d8c936bd47354945
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782879"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="724f6-102">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="724f6-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="724f6-103">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="724f6-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="724f6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="724f6-104">Methods</span></span>  
  
|<span data-ttu-id="724f6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="724f6-105">Method</span></span>|<span data-ttu-id="724f6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="724f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="724f6-107">GetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="724f6-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="724f6-108">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod) określonej przez Maska bitów.</span><span class="sxs-lookup"><span data-stu-id="724f6-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="724f6-109">GetRegistersAvailable, metoda</span><span class="sxs-lookup"><span data-stu-id="724f6-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="724f6-110">Pobiera nieco maski wskazujący, który rejestruje, w tym `ICorDebugRegisterSet` są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="724f6-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="724f6-111">GetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="724f6-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="724f6-112">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="724f6-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="724f6-113">SetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="724f6-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="724f6-114">Nie zaimplementowano dla platformy .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="724f6-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="724f6-115">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="724f6-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="724f6-116">Nie zaimplementowano dla programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="724f6-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="724f6-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="724f6-117">Remarks</span></span>  
 <span data-ttu-id="724f6-118">`ICorDebugRegisterSet` Interfejs obsługuje tylko 32-bitowych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="724f6-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="724f6-119">Użyj [icordebugregisterset2 —](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interfejsu na platformach takich jak IA-64, które wymagają dodatkowych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="724f6-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="724f6-120">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="724f6-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="724f6-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="724f6-121">Requirements</span></span>  
 <span data-ttu-id="724f6-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="724f6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="724f6-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="724f6-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="724f6-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="724f6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="724f6-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="724f6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724f6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="724f6-126">See also</span></span>

- [<span data-ttu-id="724f6-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="724f6-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="724f6-128">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="724f6-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
