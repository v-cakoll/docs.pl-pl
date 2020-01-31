---
title: ICorDebugFunction, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794503"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="3386d-102">ICorDebugFunction, interfejs</span><span class="sxs-lookup"><span data-stu-id="3386d-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="3386d-103">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="3386d-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3386d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3386d-104">Methods</span></span>  
  
|<span data-ttu-id="3386d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-105">Method</span></span>|<span data-ttu-id="3386d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3386d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3386d-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-107">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="3386d-108">Tworzy punkt przerwania na początku tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3386d-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="3386d-109">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-109">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="3386d-110">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.</span><span class="sxs-lookup"><span data-stu-id="3386d-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="3386d-111">GetCurrentVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-111">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="3386d-112">Pobiera numer wersji najnowszej edycji wykonanej w tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3386d-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="3386d-113">GetILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-113">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="3386d-114">Pobiera kod języka pośredniego firmy Microsoft (MSIL) dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3386d-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="3386d-115">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-115">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="3386d-116">Pobiera token metadanych dla zmiennej lokalnej sygnatury funkcji reprezentowanej przez to wystąpienie `ICorDebugFunction`.</span><span class="sxs-lookup"><span data-stu-id="3386d-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="3386d-117">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-117">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="3386d-118">Pobiera moduł, w którym ta funkcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="3386d-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="3386d-119">GetNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-119">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="3386d-120">Pobiera kod natywny dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3386d-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="3386d-121">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="3386d-121">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="3386d-122">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3386d-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3386d-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3386d-123">Remarks</span></span>  
 <span data-ttu-id="3386d-124">Interfejs `ICorDebugFunction` nie reprezentuje funkcji z parametrami typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3386d-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="3386d-125">Na przykład wystąpienie `ICorDebugFunction` reprezentuje `Func<T>`, ale nie `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="3386d-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="3386d-126">Wywołaj metodę [ICorDebugILFrame2:: EnumerateTypeParameters —](icordebugilframe2-enumeratetypeparameters-method.md) w celu pobrania parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="3386d-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="3386d-127">Relacja między tokenem metadanych metody, `mdMethodDef`i obiektem `ICorDebugFunction` metody jest zależna od tego, czy funkcja Edytuj i Kontynuuj jest dozwolona dla funkcji:</span><span class="sxs-lookup"><span data-stu-id="3386d-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="3386d-128">Jeśli funkcja Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego między obiektem `ICorDebugFunction` a tokenem `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="3386d-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="3386d-129">Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiektu i jeden token `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="3386d-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="3386d-130">Jeśli funkcja Edytuj i Kontynuuj jest dozwolona w funkcji, istnieje relacja wiele-do-jednego między obiektem `ICorDebugFunction` a tokenem `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="3386d-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="3386d-131">Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction`, jeden dla każdej wersji funkcji, ale tylko jeden token `mdMethodDef`.</span><span class="sxs-lookup"><span data-stu-id="3386d-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3386d-132">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="3386d-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3386d-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3386d-133">Requirements</span></span>  
 <span data-ttu-id="3386d-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3386d-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3386d-135">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3386d-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3386d-136">**Biblioteka:**  CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3386d-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="3386d-137">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3386d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3386d-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3386d-138">See also</span></span>

- [<span data-ttu-id="3386d-139">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3386d-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
