---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd0dbe1304d85c856880c989312afb11d3b554c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="89f03-102">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="89f03-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="89f03-103">Reprezentuje zarządzaną funkcję lub metodę.</span><span class="sxs-lookup"><span data-stu-id="89f03-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89f03-104">Metody</span><span class="sxs-lookup"><span data-stu-id="89f03-104">Methods</span></span>  
  
|<span data-ttu-id="89f03-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-105">Method</span></span>|<span data-ttu-id="89f03-106">Opis</span><span class="sxs-lookup"><span data-stu-id="89f03-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89f03-107">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="89f03-108">Tworzy punkt przerwania na początku tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="89f03-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="89f03-109">GetClass, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="89f03-110">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, którą ta funkcja jest elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="89f03-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="89f03-111">GetCurrentVersionNumber, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="89f03-112">Pobiera numer wersji najnowszej edycji wykonanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="89f03-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="89f03-113">GetILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="89f03-114">Pobiera kod języka pośredniego (MSIL) firmy Microsoft dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="89f03-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="89f03-115">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="89f03-116">Pobiera metadane token do lokalnej zmiennej podpisu funkcji, która jest reprezentowana przez to `ICorDebugFunction` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="89f03-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="89f03-117">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="89f03-118">Pobiera moduł, w którym ta funkcja jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="89f03-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="89f03-119">GetNativeCode, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="89f03-120">Pobiera kod natywny dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="89f03-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="89f03-121">GetToken, metoda</span><span class="sxs-lookup"><span data-stu-id="89f03-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="89f03-122">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="89f03-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89f03-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89f03-123">Remarks</span></span>  
 <span data-ttu-id="89f03-124">`ICorDebugFunction` Interfejsu nie reprezentuje funkcję z parametrami typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="89f03-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="89f03-125">Na przykład `ICorDebugFunction` reprezentuje wystąpienie `Func<T>` , ale nie `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="89f03-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="89f03-126">Wywołanie [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) można pobrać parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="89f03-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="89f03-127">Relacja między token metadanych metody, `mdMethodDef`, a także metodę `ICorDebugFunction` obiektu jest zależne od tego, czy Edytuj i Kontynuuj jest dozwolony w funkcji:</span><span class="sxs-lookup"><span data-stu-id="89f03-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="89f03-128">Jeśli Edytuj i Kontynuuj jest niedozwolone w funkcji i jeden do jednego relację między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="89f03-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="89f03-129">Oznacza to, że funkcja ma jeden `ICorDebugFunction` obiektu i jeden `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="89f03-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="89f03-130">Jeśli Edytuj i Kontynuuj jest dozwolony w funkcji, istnieje relacja wiele do jednego między `ICorDebugFunction` obiektu i `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="89f03-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="89f03-131">Oznacza to, że funkcja może mieć wielu wystąpień `ICorDebugFunction`, jeden dla każdej wersji, funkcji, ale tylko jeden `mdMethodDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="89f03-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89f03-132">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="89f03-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89f03-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89f03-133">Requirements</span></span>  
 <span data-ttu-id="89f03-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89f03-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f03-135">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89f03-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89f03-136">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89f03-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="89f03-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f03-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f03-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89f03-138">See Also</span></span>  
 [<span data-ttu-id="89f03-139">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="89f03-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
