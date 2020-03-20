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
ms.openlocfilehash: 341a86f4c1c8367f979e193a6284bf89f1b03ca0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178801"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="2ff42-102">Metoda ICorDebugILFrame4::EnumerateLocalVariablesEx</span><span class="sxs-lookup"><span data-stu-id="2ff42-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>
<span data-ttu-id="2ff42-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="2ff42-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2ff42-104">Pobiera moduł wyliczania dla zmiennej lokalnej w ramce i opcjonalnie zawiera zmienne dodane w profiler instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="2ff42-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff42-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ff42-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ff42-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ff42-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="2ff42-107">[w] Element członkowski wyliczenia [ILCodeKind,](ilcodekind-enumeration.md) który określa, czy zmienne dodane w instrumentacji ReJIT profilera są zawarte w ramce.</span><span class="sxs-lookup"><span data-stu-id="2ff42-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="2ff42-108">[na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugValueEnum", który jest wyliczaczem zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="2ff42-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff42-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ff42-109">Remarks</span></span>  
 <span data-ttu-id="2ff42-110">Ta metoda jest podobna do [Metody EnumerateLocalVariables,](icordebugilframe-enumeratelocalvariables-method.md) z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennych dodanych w instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="2ff42-110">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="2ff42-111">Ustawienie `flags` `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span><span class="sxs-lookup"><span data-stu-id="2ff42-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="2ff42-112">`flags` Ustawienie, `ILCODE_REJIT_IL` aby umożliwia debugerowi dostęp do zmiennych lokalnych dodanych w profiler Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="2ff42-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="2ff42-113">Jeśli język pośredni (IL) nie jest instrumentowany, wyliczenie `S_OK`jest puste, a metoda zwraca .</span><span class="sxs-lookup"><span data-stu-id="2ff42-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="2ff42-114">Wyliczacz może nie zawierać wszystkie zmienne lokalne w uruchomionej metody, ponieważ niektóre z nich mogą nie być aktywne.</span><span class="sxs-lookup"><span data-stu-id="2ff42-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff42-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ff42-115">Requirements</span></span>  
 <span data-ttu-id="2ff42-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff42-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff42-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ff42-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ff42-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ff42-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ff42-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff42-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff42-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ff42-120">See also</span></span>

- [<span data-ttu-id="2ff42-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ff42-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="2ff42-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2ff42-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2ff42-123">ReJIT: Poradnik</span><span class="sxs-lookup"><span data-stu-id="2ff42-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
