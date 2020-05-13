---
title: ICorDebugModule, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212246"
---
# <a name="icordebugmodule-interface"></a><span data-ttu-id="2857d-102">ICorDebugModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="2857d-102">ICorDebugModule Interface</span></span>

<span data-ttu-id="2857d-103">Reprezentuje moduł środowiska uruchomieniowego języka wspólnego (CLR), który jest plikiem wykonywalnym lub biblioteką dołączaną dynamicznie (DLL).</span><span class="sxs-lookup"><span data-stu-id="2857d-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2857d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2857d-104">Methods</span></span>  
  
|<span data-ttu-id="2857d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-105">Method</span></span>|<span data-ttu-id="2857d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2857d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2857d-107">CreateBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-107">CreateBreakpoint Method</span></span>](icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="2857d-108">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="2857d-108">Not implemented.</span></span>|  
|[<span data-ttu-id="2857d-109">EnableClassLoadCallbacks, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-109">EnableClassLoadCallbacks Method</span></span>](icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="2857d-110">Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-110">Determines whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="2857d-111">EnableJITDebugging, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-111">EnableJITDebugging Method</span></span>](icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="2857d-112">Określa, czy kompilator just in Time (JIT) zachowuje informacje debugowania dla metod w ramach tego modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="2857d-113">GetAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-113">GetAssembly Method</span></span>](icordebugmodule-getassembly-method.md)|<span data-ttu-id="2857d-114">Pobiera zawierający go zestaw dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="2857d-115">GetBaseAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-115">GetBaseAddress Method</span></span>](icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="2857d-116">Pobiera adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="2857d-117">GetClassFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-117">GetClassFromToken Method</span></span>](icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="2857d-118">Pobiera ICorDebugClass z metadanych.</span><span class="sxs-lookup"><span data-stu-id="2857d-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="2857d-119">GetEditAndContinueSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-119">GetEditAndContinueSnapshot Method</span></span>](icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="2857d-120">Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="2857d-120">Deprecated.</span></span>|  
|[<span data-ttu-id="2857d-121">GetFunctionFromRVA, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-121">GetFunctionFromRVA Method</span></span>](icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="2857d-122">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="2857d-122">Not implemented.</span></span>|  
|[<span data-ttu-id="2857d-123">GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-123">GetFunctionFromToken Method</span></span>](icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="2857d-124">Pobiera funkcję określoną przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="2857d-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="2857d-125">GetGlobalVariableValue, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-125">GetGlobalVariableValue Method</span></span>](icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="2857d-126">Pobiera obiekt wartości dla określonej zmiennej globalnej.</span><span class="sxs-lookup"><span data-stu-id="2857d-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="2857d-127">GetMetaDataInterface, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-127">GetMetaDataInterface Method</span></span>](icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="2857d-128">Pobiera wskaźnik interfejsu metadanych, którego można użyć do sprawdzenia metadanych dla modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="2857d-129">GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-129">GetName Method</span></span>](icordebugmodule-getname-method.md)|<span data-ttu-id="2857d-130">Pobiera nazwę pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="2857d-131">GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-131">GetProcess Method</span></span>](icordebugmodule-getprocess-method.md)|<span data-ttu-id="2857d-132">Pobiera proces zawierający dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="2857d-133">GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-133">GetSize Method</span></span>](icordebugmodule-getsize-method.md)|<span data-ttu-id="2857d-134">Pobiera rozmiar modułu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2857d-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="2857d-135">GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-135">GetToken Method</span></span>](icordebugmodule-gettoken-method.md)|<span data-ttu-id="2857d-136">Pobiera token dla wpisu tabeli dla tego modułu.</span><span class="sxs-lookup"><span data-stu-id="2857d-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="2857d-137">IsDynamic, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-137">IsDynamic Method</span></span>](icordebugmodule-isdynamic-method.md)|<span data-ttu-id="2857d-138">Wskazuje, czy moduł jest dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="2857d-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="2857d-139">IsInMemory, metoda</span><span class="sxs-lookup"><span data-stu-id="2857d-139">IsInMemory Method</span></span>](icordebugmodule-isinmemory-method.md)|<span data-ttu-id="2857d-140">Wskazuje, czy ten moduł istnieje tylko w pamięci.</span><span class="sxs-lookup"><span data-stu-id="2857d-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2857d-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2857d-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2857d-142">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2857d-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2857d-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2857d-143">Requirements</span></span>  
 <span data-ttu-id="2857d-144">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2857d-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2857d-145">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2857d-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2857d-146">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2857d-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2857d-147">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2857d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2857d-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2857d-148">See also</span></span>

- [<span data-ttu-id="2857d-149">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2857d-149">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="2857d-150">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2857d-150">Debugging Interfaces</span></span>](debugging-interfaces.md)
