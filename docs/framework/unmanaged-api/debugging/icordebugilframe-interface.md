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
ms.openlocfilehash: 7a27b8ec512498c7bf817aca36267c37d8070a4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788580"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="6139a-102">ICorDebugILFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="6139a-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="6139a-103">Przedstawia ramkę stosu kodu języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="6139a-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="6139a-104">Ten interfejs jest podklasą interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="6139a-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6139a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6139a-105">Methods</span></span>  
  
|<span data-ttu-id="6139a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-106">Method</span></span>|<span data-ttu-id="6139a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6139a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6139a-108">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="6139a-109">Pobiera wartość wskazującą, czy jest bezpieczna, aby ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="6139a-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="6139a-110">EnumerateArguments, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="6139a-111">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="6139a-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="6139a-112">EnumerateLocalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="6139a-113">Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="6139a-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="6139a-114">GetArgument, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="6139a-115">Pobiera wartość określonego argumentu w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="6139a-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="6139a-116">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="6139a-117">Pobiera wartość wskaźnika instrukcji i wartość kombinacji bitowej opisującą sposób uzyskiwania wartości wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6139a-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="6139a-118">GetLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="6139a-119">Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="6139a-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="6139a-120">GetStackDepth, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="6139a-121">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="6139a-121">Not implemented.</span></span>|  
|[<span data-ttu-id="6139a-122">GetStackValue, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="6139a-123">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="6139a-123">Not implemented.</span></span>|  
|[<span data-ttu-id="6139a-124">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="6139a-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="6139a-125">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="6139a-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6139a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6139a-126">Remarks</span></span>  
 <span data-ttu-id="6139a-127">Interfejs `ICorDebugILFrame` jest wyspecjalizowanym interfejsem ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="6139a-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="6139a-128">Jest używana w przypadku ramek kodu MSIL lub dla ramek skompilowanych w trybie just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="6139a-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="6139a-129">Ramki skompilowane JIT implementują zarówno interfejs `ICorDebugILFrame`, jak i interfejs ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="6139a-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6139a-130">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6139a-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6139a-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6139a-131">Requirements</span></span>  
 <span data-ttu-id="6139a-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6139a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6139a-133">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6139a-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6139a-134">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6139a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6139a-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6139a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6139a-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6139a-136">See also</span></span>

- [<span data-ttu-id="6139a-137">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6139a-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
