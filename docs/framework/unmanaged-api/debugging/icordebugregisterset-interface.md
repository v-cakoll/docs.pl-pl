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
ms.openlocfilehash: 7c60fa775b82372b50d1eb3891f107b97df3e73a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378270"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="e5b06-102">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5b06-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="e5b06-103">Reprezentuje zestaw rejestrów dostępnych na komputerze, który aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="e5b06-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5b06-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e5b06-104">Methods</span></span>  
  
|<span data-ttu-id="e5b06-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e5b06-105">Method</span></span>|<span data-ttu-id="e5b06-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e5b06-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5b06-107">GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5b06-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="e5b06-108">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.</span><span class="sxs-lookup"><span data-stu-id="e5b06-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="e5b06-109">GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5b06-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="e5b06-110">Pobiera maskę bitową wskazującą, które rejestry w tej `ICorDebugRegisterSet` chwili są dostępne.</span><span class="sxs-lookup"><span data-stu-id="e5b06-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="e5b06-111">GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="e5b06-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="e5b06-112">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="e5b06-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="e5b06-113">SetRegisters, metoda</span><span class="sxs-lookup"><span data-stu-id="e5b06-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="e5b06-114">Nie zaimplementowane dla .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="e5b06-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="e5b06-115">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="e5b06-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="e5b06-116">Nie zaimplementowane dla .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="e5b06-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5b06-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5b06-117">Remarks</span></span>  
 <span data-ttu-id="e5b06-118">`ICorDebugRegisterSet`Interfejs obsługuje tylko rejestry 32-bitowe.</span><span class="sxs-lookup"><span data-stu-id="e5b06-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="e5b06-119">Użyj interfejsu [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) na platformach, takich jak IA-64, które wymagają dodatkowych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="e5b06-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5b06-120">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e5b06-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b06-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5b06-121">Requirements</span></span>  
 <span data-ttu-id="e5b06-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b06-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b06-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5b06-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5b06-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5b06-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5b06-125">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b06-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b06-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5b06-126">See also</span></span>

- [<span data-ttu-id="e5b06-127">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e5b06-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e5b06-128">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5b06-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
