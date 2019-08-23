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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917209"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="06ce2-102">ICorDebugFunction, interfejs</span><span class="sxs-lookup"><span data-stu-id="06ce2-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="06ce2-103">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="06ce2-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06ce2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="06ce2-104">Methods</span></span>  
  
|<span data-ttu-id="06ce2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-105">Method</span></span>|<span data-ttu-id="06ce2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="06ce2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06ce2-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="06ce2-108">Tworzy punkt przerwania na początku tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="06ce2-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="06ce2-109">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="06ce2-110">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.</span><span class="sxs-lookup"><span data-stu-id="06ce2-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="06ce2-111">GetCurrentVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="06ce2-112">Pobiera numer wersji najnowszej edycji wykonanej w tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="06ce2-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="06ce2-113">GetILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="06ce2-114">Pobiera kod języka pośredniego firmy Microsoft (MSIL) dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="06ce2-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="06ce2-115">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="06ce2-116">Pobiera token metadanych dla zmiennej lokalnej sygnatury funkcji reprezentowanej przez to `ICorDebugFunction` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="06ce2-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="06ce2-117">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="06ce2-118">Pobiera moduł, w którym ta funkcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="06ce2-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="06ce2-119">GetNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="06ce2-120">Pobiera kod natywny dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="06ce2-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="06ce2-121">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="06ce2-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="06ce2-122">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="06ce2-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06ce2-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06ce2-123">Remarks</span></span>  
 <span data-ttu-id="06ce2-124">`ICorDebugFunction` Interfejs nie reprezentuje funkcji z parametrami typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="06ce2-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="06ce2-125">Na przykład `ICorDebugFunction` wystąpienie może reprezentować `Func<T>` , ale `Func<string>`nie.</span><span class="sxs-lookup"><span data-stu-id="06ce2-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="06ce2-126">Wywołaj metodę [ICorDebugILFrame2:: EnumerateTypeParameters —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) w celu pobrania parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="06ce2-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="06ce2-127">Relacja między tokenem `mdMethodDef`metadanych metody a `ICorDebugFunction` obiektem metody jest zależna od tego, czy funkcja Edytuj i Kontynuuj jest dozwolona dla funkcji:</span><span class="sxs-lookup"><span data-stu-id="06ce2-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="06ce2-128">Jeśli funkcja Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego między `ICorDebugFunction` obiektem `mdMethodDef` a tokenem.</span><span class="sxs-lookup"><span data-stu-id="06ce2-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="06ce2-129">Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiekt i jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="06ce2-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="06ce2-130">Jeśli funkcja Edytuj i Kontynuuj jest dozwolona w funkcji, istnieje relacja wiele-do-jednego między `ICorDebugFunction` obiektem `mdMethodDef` a tokenem.</span><span class="sxs-lookup"><span data-stu-id="06ce2-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="06ce2-131">Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction`, jeden dla każdej wersji funkcji, ale tylko jeden `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="06ce2-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06ce2-132">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="06ce2-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06ce2-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06ce2-133">Requirements</span></span>  
 <span data-ttu-id="06ce2-134">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06ce2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06ce2-135">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06ce2-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06ce2-136">**Biblioteki**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06ce2-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="06ce2-137">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06ce2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ce2-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06ce2-138">See also</span></span>

- [<span data-ttu-id="06ce2-139">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="06ce2-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
