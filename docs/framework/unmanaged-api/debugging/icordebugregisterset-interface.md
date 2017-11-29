---
title: "ICorDebugRegisterSet — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ccff205758dee2ffc6a6432ab20b3310147eb06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="665ca-102">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="665ca-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="665ca-103">Reprezentuje zestaw rejestry dostępne na komputerze, który jest w trakcie wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="665ca-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="665ca-104">Metody</span><span class="sxs-lookup"><span data-stu-id="665ca-104">Methods</span></span>  
  
|<span data-ttu-id="665ca-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="665ca-105">Method</span></span>|<span data-ttu-id="665ca-106">Opis</span><span class="sxs-lookup"><span data-stu-id="665ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="665ca-107">GetRegisters — metoda</span><span class="sxs-lookup"><span data-stu-id="665ca-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="665ca-108">Pobiera wartość każdego rejestru (na komputerze, który jest aktualnie wykonywany kodu) określonym przez maska bitowa.</span><span class="sxs-lookup"><span data-stu-id="665ca-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="665ca-109">GetRegistersAvailable — metoda</span><span class="sxs-lookup"><span data-stu-id="665ca-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="665ca-110">Pobiera bit maski wskazujący, który rejestruje w tym `ICorDebugRegisterSet` są obecnie dostępne.</span><span class="sxs-lookup"><span data-stu-id="665ca-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="665ca-111">GetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="665ca-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="665ca-112">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="665ca-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="665ca-113">SetRegisters — metoda</span><span class="sxs-lookup"><span data-stu-id="665ca-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="665ca-114">Nie zaimplementowano dla platformy .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="665ca-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="665ca-115">SetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="665ca-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="665ca-116">Nie zaimplementowano dla programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="665ca-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="665ca-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="665ca-117">Remarks</span></span>  
 <span data-ttu-id="665ca-118">`ICorDebugRegisterSet` Interfejs obsługuje tylko 32-bitowych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="665ca-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="665ca-119">Użyj [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interfejsu na platformach takich jak IA-64, które wymagają dodatkowych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="665ca-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="665ca-120">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="665ca-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="665ca-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="665ca-121">Requirements</span></span>  
 <span data-ttu-id="665ca-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="665ca-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="665ca-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="665ca-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="665ca-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="665ca-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="665ca-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="665ca-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665ca-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="665ca-126">See Also</span></span>  
 [<span data-ttu-id="665ca-127">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="665ca-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="665ca-128">ICorDebugRegisterSet2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="665ca-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
