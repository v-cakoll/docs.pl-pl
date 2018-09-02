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
ms.openlocfilehash: 7ba61a91f2296d6e5cc795c3775bb72247e34a56
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43453105"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="c5de5-102">Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="c5de5-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="c5de5-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="c5de5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c5de5-104">Pobiera moduł wyliczający dla zmiennej lokalnej w ramce i opcjonalnie zawiera zmienne, które dodano w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="c5de5-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5de5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5de5-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5de5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5de5-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="c5de5-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) składowej wyliczenia, która określa, czy zmienne dodany do programu profilującego Instrumentację ReJIT znajdują się w ramce.</span><span class="sxs-lookup"><span data-stu-id="c5de5-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="c5de5-108">[out] Wskaźnik na adres obiektu "icordebugvalueenum —", który jest moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="c5de5-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5de5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5de5-109">Remarks</span></span>  
 <span data-ttu-id="c5de5-110">Ta metoda jest podobna do [enumeratelocalvariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) metody, z wyjątkiem tego opcjonalnie uzyskuje dostęp dodany do programu profilującego Instrumentację ReJIT zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c5de5-110">This method is similar to the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="c5de5-111">Ustawienie `flags` do `ILCODE_ORIGINAL_IL` jest równoważne z wywoływaniem [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="c5de5-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="c5de5-112">Ustawienie `flags` do `ILCODE_REJIT_IL` pozwala debugerowi na dostęp do zmiennych lokalnych, dodane w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="c5de5-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="c5de5-113">Jeśli nie ma instrumentacji języka pośredniego (IL), wyliczenia jest pusty, a metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="c5de5-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="c5de5-114">Moduł wyliczający może nie obejmować wszystkich zmiennych lokalnych w metodzie uruchomione, ponieważ niektóre z nich nie może być aktywne.</span><span class="sxs-lookup"><span data-stu-id="c5de5-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5de5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5de5-115">Requirements</span></span>  
 <span data-ttu-id="c5de5-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5de5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5de5-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5de5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5de5-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5de5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5de5-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5de5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5de5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5de5-120">See Also</span></span>  
 [<span data-ttu-id="c5de5-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5de5-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="c5de5-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c5de5-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c5de5-123">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="c5de5-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
