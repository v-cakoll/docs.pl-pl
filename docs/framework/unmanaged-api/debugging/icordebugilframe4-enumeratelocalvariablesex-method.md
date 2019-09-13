---
title: Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3deb497c3e842e25bcaa46a867dd61ea4a1c3804
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926817"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="765a3-102">Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="765a3-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="765a3-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="765a3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="765a3-104">Pobiera moduł wyliczający dla zmiennej lokalnej w ramce i opcjonalnie zawiera zmienne dodane w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="765a3-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="765a3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="765a3-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="765a3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="765a3-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="765a3-107">podczas Element członkowski wyliczenia [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , który określa, czy zmienne dodane w Instrumentacji ReJIT profilera są zawarte w ramce.</span><span class="sxs-lookup"><span data-stu-id="765a3-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="765a3-108">określoną Wskaźnik do adresu obiektu "ICorDebugValueEnum", który jest modułem wyliczającym dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="765a3-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="765a3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="765a3-109">Remarks</span></span>  
 <span data-ttu-id="765a3-110">Ta metoda jest podobna do metody [EnumerateLocalVariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennych dodanych w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="765a3-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="765a3-111">Ustawienie `flags` jest równoważne wywołaniu [ICorDebugILFrame:: EnumerateLocalVariables —.](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) `ILCODE_ORIGINAL_IL`</span><span class="sxs-lookup"><span data-stu-id="765a3-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="765a3-112">Ustawienie `flags`pozwaladebugerowi nadostępdozmiennychlokalnychdodanychwInstrumentacjiReJITprofilera.`ILCODE_REJIT_IL`</span><span class="sxs-lookup"><span data-stu-id="765a3-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="765a3-113">Jeśli język pośredni (IL) nie ma instrumentacji, Wyliczenie jest puste i metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="765a3-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="765a3-114">Moduł wyliczający nie może zawierać wszystkich zmiennych lokalnych w uruchomionej metodzie, ponieważ niektóre z nich mogą nie być aktywne.</span><span class="sxs-lookup"><span data-stu-id="765a3-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="765a3-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="765a3-115">Requirements</span></span>  
 <span data-ttu-id="765a3-116">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="765a3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="765a3-117">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="765a3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="765a3-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="765a3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="765a3-119">**.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="765a3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="765a3-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="765a3-120">See also</span></span>

- [<span data-ttu-id="765a3-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="765a3-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="765a3-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="765a3-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="765a3-123">ReJIT: Przewodnik krok po kroku</span><span class="sxs-lookup"><span data-stu-id="765a3-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
