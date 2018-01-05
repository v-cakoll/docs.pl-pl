---
title: Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c82ecd9045deb772e31e549bf1050f85b148fd0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="5c833-102">Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="5c833-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="5c833-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="5c833-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5c833-104">Pobiera moduł wyliczający dla zmiennej lokalnej w ramce i opcjonalnie zawiera zmienne dodane w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="5c833-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c833-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c833-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c833-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c833-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="5c833-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) element członkowski wyliczenia, która określa, czy zmienne dodane w ReJIT Instrumentacji profilera znajdują się w ramce.</span><span class="sxs-lookup"><span data-stu-id="5c833-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="5c833-108">[out] Wskaźnik do adres obiektu "ICorDebugValueEnum", który moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="5c833-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c833-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c833-109">Remarks</span></span>  
 <span data-ttu-id="5c833-110">Ta metoda jest podobna do [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) metody, z wyjątkiem, że opcjonalnie dostęp do zmiennych dodane w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="5c833-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="5c833-111">Ustawienie `flags` do `ILCODE_ORIGINAL_IL` jest odpowiednikiem wywołania [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="5c833-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="5c833-112">Ustawienie `flags` do `ILCODE_REJIT_IL` umożliwia debugera tak, aby mieć dostęp do zmiennych lokalnych dodane w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="5c833-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="5c833-113">Jeśli nie został zinstrumentowany na języku pośrednim (IL), wyliczenie jest pusty i metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="5c833-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="5c833-114">Moduł wyliczający nie może zawierać wszystkich zmiennych lokalnych w metodzie uruchomione, ponieważ niektóre z nich nie może być aktywny.</span><span class="sxs-lookup"><span data-stu-id="5c833-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c833-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c833-115">Requirements</span></span>  
 <span data-ttu-id="5c833-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c833-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c833-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c833-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c833-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c833-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c833-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c833-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c833-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c833-120">See Also</span></span>  
 [<span data-ttu-id="5c833-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c833-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="5c833-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5c833-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5c833-123">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="5c833-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
