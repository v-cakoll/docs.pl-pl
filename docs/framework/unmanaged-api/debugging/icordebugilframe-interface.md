---
title: ICorDebugILFrame — Interfejs
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
ms.openlocfilehash: 01c247f838f66d1a77831755126a5a1f56870c1e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095147"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="20444-102">ICorDebugILFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="20444-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="20444-103">Przedstawia ramkę stosu kodu języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="20444-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="20444-104">Ten interfejs jest podklasą interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="20444-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20444-105">Metody</span><span class="sxs-lookup"><span data-stu-id="20444-105">Methods</span></span>  
  
|<span data-ttu-id="20444-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="20444-106">Method</span></span>|<span data-ttu-id="20444-107">Opis</span><span class="sxs-lookup"><span data-stu-id="20444-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20444-108">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="20444-109">Pobiera wartość wskazującą, czy jest bezpieczna, aby ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="20444-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="20444-110">EnumerateArguments, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="20444-111">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="20444-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="20444-112">EnumerateLocalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="20444-113">Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="20444-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="20444-114">GetArgument, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="20444-115">Pobiera wartość określonego argumentu w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="20444-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="20444-116">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="20444-117">Pobiera wartość wskaźnika instrukcji i wartość kombinacji bitowej opisującą sposób uzyskiwania wartości wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="20444-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="20444-118">GetLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="20444-119">Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="20444-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="20444-120">GetStackDepth, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="20444-121">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="20444-121">Not implemented.</span></span>|  
|[<span data-ttu-id="20444-122">GetStackValue, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="20444-123">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="20444-123">Not implemented.</span></span>|  
|[<span data-ttu-id="20444-124">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="20444-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="20444-125">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="20444-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20444-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20444-126">Remarks</span></span>  
 <span data-ttu-id="20444-127">Interfejs `ICorDebugILFrame` jest wyspecjalizowanym interfejsem ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="20444-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="20444-128">Jest używana w przypadku ramek kodu MSIL lub dla ramek skompilowanych w trybie just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="20444-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="20444-129">Ramki skompilowane JIT implementują zarówno interfejs `ICorDebugILFrame`, jak i interfejs ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="20444-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20444-130">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="20444-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20444-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20444-131">Requirements</span></span>  
 <span data-ttu-id="20444-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20444-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20444-133">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20444-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20444-134">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="20444-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20444-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20444-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20444-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20444-136">See also</span></span>

- [<span data-ttu-id="20444-137">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="20444-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
