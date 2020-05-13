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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213247"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="7ce67-102">ICorDebugFunction, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ce67-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="7ce67-103">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="7ce67-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ce67-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ce67-104">Methods</span></span>  
  
|<span data-ttu-id="7ce67-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-105">Method</span></span>|<span data-ttu-id="7ce67-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7ce67-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ce67-107">CreateBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-107">CreateBreakpoint Method</span></span>](icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="7ce67-108">Tworzy punkt przerwania na początku tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ce67-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="7ce67-109">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-109">GetClass Method</span></span>](icordebugfunction-getclass-method.md)|<span data-ttu-id="7ce67-110">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.</span><span class="sxs-lookup"><span data-stu-id="7ce67-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="7ce67-111">GetCurrentVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-111">GetCurrentVersionNumber Method</span></span>](icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="7ce67-112">Pobiera numer wersji najnowszej edycji wykonanej w tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ce67-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="7ce67-113">GetILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-113">GetILCode Method</span></span>](icordebugfunction-getilcode-method.md)|<span data-ttu-id="7ce67-114">Pobiera kod języka pośredniego firmy Microsoft (MSIL) dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ce67-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="7ce67-115">GetLocalVarSigToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-115">GetLocalVarSigToken Method</span></span>](icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="7ce67-116">Pobiera token metadanych dla zmiennej lokalnej sygnatury funkcji reprezentowanej przez to `ICorDebugFunction` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="7ce67-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="7ce67-117">GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-117">GetModule Method</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="7ce67-118">Pobiera moduł, w którym ta funkcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="7ce67-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="7ce67-119">GetNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-119">GetNativeCode Method</span></span>](icordebugfunction-getnativecode-method.md)|<span data-ttu-id="7ce67-120">Pobiera kod natywny dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ce67-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="7ce67-121">GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="7ce67-121">GetToken Method</span></span>](icordebugfunction-gettoken-method.md)|<span data-ttu-id="7ce67-122">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="7ce67-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ce67-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ce67-123">Remarks</span></span>  
 <span data-ttu-id="7ce67-124">`ICorDebugFunction`Interfejs nie reprezentuje funkcji z parametrami typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7ce67-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="7ce67-125">Na przykład `ICorDebugFunction` wystąpienie może reprezentować, `Func<T>` ale nie `Func<string>` .</span><span class="sxs-lookup"><span data-stu-id="7ce67-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="7ce67-126">Wywołaj metodę [ICorDebugILFrame2:: EnumerateTypeParameters —](icordebugilframe2-enumeratetypeparameters-method.md) w celu pobrania parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7ce67-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="7ce67-127">Relacja między tokenem metadanych metody `mdMethodDef` a `ICorDebugFunction` obiektem metody jest zależna od tego, czy funkcja Edytuj i Kontynuuj jest dozwolona dla funkcji:</span><span class="sxs-lookup"><span data-stu-id="7ce67-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="7ce67-128">Jeśli funkcja Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego między `ICorDebugFunction` obiektem a `mdMethodDef` tokenem.</span><span class="sxs-lookup"><span data-stu-id="7ce67-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="7ce67-129">Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiekt i jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="7ce67-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="7ce67-130">Jeśli funkcja Edytuj i Kontynuuj jest dozwolona w funkcji, istnieje relacja wiele-do-jednego między `ICorDebugFunction` obiektem a `mdMethodDef` tokenem.</span><span class="sxs-lookup"><span data-stu-id="7ce67-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="7ce67-131">Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction` , jeden dla każdej wersji funkcji, ale tylko jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="7ce67-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ce67-132">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="7ce67-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ce67-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ce67-133">Requirements</span></span>  
 <span data-ttu-id="7ce67-134">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ce67-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ce67-135">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ce67-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ce67-136">**Biblioteka:**  CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7ce67-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ce67-137">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ce67-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce67-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ce67-138">See also</span></span>

- [<span data-ttu-id="7ce67-139">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7ce67-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
