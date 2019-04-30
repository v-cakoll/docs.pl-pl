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
ms.openlocfilehash: ca21911f3d16b79887b9d6d8185f8fab17651321
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672994"
---
# <a name="icordebugfunction-interface"></a><span data-ttu-id="e4f81-102">ICorDebugFunction, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4f81-102">ICorDebugFunction Interface</span></span>

<span data-ttu-id="e4f81-103">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="e4f81-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4f81-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e4f81-104">Methods</span></span>  
  
|<span data-ttu-id="e4f81-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-105">Method</span></span>|<span data-ttu-id="e4f81-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e4f81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4f81-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="e4f81-108">Tworzy punkt przerwania na początku tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4f81-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="e4f81-109">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="e4f81-110">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, którą ta funkcja jest elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="e4f81-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="e4f81-111">GetCurrentVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="e4f81-112">Pobiera numer wersji najnowszej edycji wykonanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4f81-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="e4f81-113">GetILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="e4f81-114">Pobiera kod intermediate language (MSIL) firmy Microsoft dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4f81-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="e4f81-115">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="e4f81-116">Pobiera token metadanych lokalnej zmiennej podpis funkcji, który jest reprezentowany przez ten `ICorDebugFunction` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e4f81-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="e4f81-117">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="e4f81-118">Pobiera moduł, w którym ta funkcja jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="e4f81-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="e4f81-119">GetNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="e4f81-120">Pobiera kodu natywnego dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4f81-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="e4f81-121">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="e4f81-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="e4f81-122">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e4f81-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4f81-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4f81-123">Remarks</span></span>  
 <span data-ttu-id="e4f81-124">`ICorDebugFunction` Interfejsu nie reprezentuje funkcję z parametrami typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="e4f81-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="e4f81-125">Na przykład `ICorDebugFunction` reprezentuje wystąpienie `Func<T>` , ale nie `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="e4f81-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="e4f81-126">Wywołaj [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) można pobrać parametrów typu genetycznego.</span><span class="sxs-lookup"><span data-stu-id="e4f81-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="e4f81-127">Relacja między tokenu metadanych metody `mdMethodDef`i metodę `ICorDebugFunction` obiekt jest zależny od tego, czy Edytuj i Kontynuuj jest dozwolona w funkcji:</span><span class="sxs-lookup"><span data-stu-id="e4f81-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
- <span data-ttu-id="e4f81-128">Jeśli Edytuj i Kontynuuj nie jest dozwolona w funkcji, istnieje relacja jeden do jednego, między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="e4f81-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="e4f81-129">Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiektu i jeden `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="e4f81-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
- <span data-ttu-id="e4f81-130">Jeśli Edytuj i Kontynuuj jest dozwolony dla funkcji, istnieje relacja wiele do jednego między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="e4f81-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="e4f81-131">Oznacza to, że funkcja może mieć wiele wystąpień `ICorDebugFunction`, jeden dla każdej wersji funkcji, ale tylko jeden `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="e4f81-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4f81-132">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="e4f81-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f81-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4f81-133">Requirements</span></span>  
 <span data-ttu-id="e4f81-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4f81-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f81-135">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4f81-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4f81-136">**Biblioteka:**  CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4f81-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4f81-137">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f81-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f81-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4f81-138">See also</span></span>

- [<span data-ttu-id="e4f81-139">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e4f81-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
