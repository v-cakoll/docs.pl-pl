---
title: ICorDebugILFrame, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a40436fcf1485c5d08d175b0396af2b6870c19a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917021"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="aeca9-102">ICorDebugILFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="aeca9-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="aeca9-103">Przedstawia ramkę stosu kodu języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="aeca9-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="aeca9-104">Ten interfejs jest podklasą interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="aeca9-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeca9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aeca9-105">Methods</span></span>  
  
|<span data-ttu-id="aeca9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-106">Method</span></span>|<span data-ttu-id="aeca9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="aeca9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeca9-108">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="aeca9-109">Pobiera wartość wskazującą, czy jest bezpieczna, aby ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="aeca9-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="aeca9-110">EnumerateArguments, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="aeca9-111">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="aeca9-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="aeca9-112">EnumerateLocalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="aeca9-113">Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="aeca9-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="aeca9-114">GetArgument, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="aeca9-115">Pobiera wartość określonego argumentu w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="aeca9-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="aeca9-116">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="aeca9-117">Pobiera wartość wskaźnika instrukcji i wartość kombinacji bitowej opisującą sposób uzyskiwania wartości wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="aeca9-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="aeca9-118">GetLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="aeca9-119">Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="aeca9-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="aeca9-120">GetStackDepth, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="aeca9-121">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="aeca9-121">Not implemented.</span></span>|  
|[<span data-ttu-id="aeca9-122">GetStackValue, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="aeca9-123">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="aeca9-123">Not implemented.</span></span>|  
|[<span data-ttu-id="aeca9-124">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="aeca9-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="aeca9-125">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="aeca9-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeca9-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aeca9-126">Remarks</span></span>  
 <span data-ttu-id="aeca9-127">`ICorDebugILFrame` Interfejs jest wyspecjalizowanym interfejsem ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="aeca9-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="aeca9-128">Jest używana w przypadku ramek kodu MSIL lub dla ramek skompilowanych w trybie just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="aeca9-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="aeca9-129">Ramki skompilowane JIT implementują `ICorDebugILFrame` interfejs i interfejs ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="aeca9-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeca9-130">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="aeca9-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeca9-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aeca9-131">Requirements</span></span>  
 <span data-ttu-id="aeca9-132">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeca9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeca9-133">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeca9-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeca9-134">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeca9-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeca9-135">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeca9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeca9-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aeca9-136">See also</span></span>

- [<span data-ttu-id="aeca9-137">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="aeca9-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
