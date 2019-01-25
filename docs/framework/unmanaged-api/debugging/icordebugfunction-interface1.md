---
title: ICorDebugFunction Interface1
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
ms.openlocfilehash: b810ce8634781438faccac25f96442624a78ea0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676773"
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="f0bf1-102">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="f0bf1-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="f0bf1-103">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0bf1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f0bf1-104">Methods</span></span>  
  
|<span data-ttu-id="f0bf1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-105">Method</span></span>|<span data-ttu-id="f0bf1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f0bf1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0bf1-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="f0bf1-108">Tworzy punkt przerwania na początku tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="f0bf1-109">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="f0bf1-110">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, którą ta funkcja jest elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="f0bf1-111">GetCurrentVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="f0bf1-112">Pobiera numer wersji najnowszej edycji wykonanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="f0bf1-113">GetILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="f0bf1-114">Pobiera kod intermediate language (MSIL) firmy Microsoft dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="f0bf1-115">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="f0bf1-116">Pobiera token metadanych lokalnej zmiennej podpis funkcji, który jest reprezentowany przez ten `ICorDebugFunction` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="f0bf1-117">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="f0bf1-118">Pobiera moduł, w którym ta funkcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="f0bf1-119">GetNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="f0bf1-120">Pobiera kodu natywnego dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="f0bf1-121">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="f0bf1-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="f0bf1-122">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0bf1-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0bf1-123">Remarks</span></span>  
 <span data-ttu-id="f0bf1-124">`ICorDebugFunction` Interfejsu nie reprezentuje funkcję z parametrami typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="f0bf1-125">Na przykład `ICorDebugFunction` reprezentuje wystąpienie `Func<T>` , ale nie `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="f0bf1-126">Wywołaj [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) można pobrać parametrów typu genetycznego.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="f0bf1-127">Relacja między tokenu metadanych metody `mdMethodDef`i metodę `ICorDebugFunction` obiekt jest zależny od tego, czy Edytuj i Kontynuuj jest dozwolona w funkcji:</span><span class="sxs-lookup"><span data-stu-id="f0bf1-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="f0bf1-128">Jeśli Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego, między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f0bf1-129">Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiektu i jeden `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="f0bf1-130">Jeśli Edytuj i Kontynuuj jest dozwolony dla funkcji, istnieje relacja wiele do jednego między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="f0bf1-131">Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction`, jeden dla każdej wersji funkcji, ale tylko jeden `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0bf1-132">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="f0bf1-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0bf1-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0bf1-133">Requirements</span></span>  
 <span data-ttu-id="f0bf1-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0bf1-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0bf1-135">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0bf1-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0bf1-136">**Biblioteka:**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0bf1-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0bf1-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0bf1-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0bf1-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0bf1-138">See also</span></span>
- [<span data-ttu-id="f0bf1-139">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0bf1-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
