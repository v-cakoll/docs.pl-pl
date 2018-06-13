---
title: Metoda ICorDebugILFrame4::GetLocalVariableEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a82f092a0f10fd621ac4facdee201fa239e1c1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414532"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="be996-102">Metoda ICorDebugILFrame4::GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="be996-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="be996-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="be996-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="be996-104">Pobiera wartość zmiennej lokalnej określony w tej ramki stosu w języku pośrednim (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodane w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="be996-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be996-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="be996-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be996-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="be996-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="be996-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) element członkowski wyliczenia, która określa, czy zmienna dodane w ReJIT Instrumentacji profilera znajduje się w ramce.</span><span class="sxs-lookup"><span data-stu-id="be996-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="be996-108">[in] Indeks zmiennej lokalnej w ramce stosu IL.</span><span class="sxs-lookup"><span data-stu-id="be996-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="be996-109">[out] Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobrana wartość.</span><span class="sxs-lookup"><span data-stu-id="be996-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be996-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be996-110">Remarks</span></span>  
 <span data-ttu-id="be996-111">Ta metoda jest podobna do [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody, z wyjątkiem, że opcjonalnie dostęp do zmiennej dodane w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="be996-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="be996-112">Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest odpowiednikiem wywołania [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); w wypadku metody są instrumentowane przy użyciu dodatkowych zmiennych lokalnych, nie można uzyskać dostępu do tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="be996-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="be996-113">`ILCODE_REJIT_IL` Umożliwia debugera tak, aby mieć dostęp do zmiennych lokalnych dodane w ReJIT Instrumentacji profilera.</span><span class="sxs-lookup"><span data-stu-id="be996-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="be996-114">Jeśli nie ma instrumentacji IL, metoda zwraca `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="be996-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be996-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be996-115">Requirements</span></span>  
 <span data-ttu-id="be996-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be996-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be996-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be996-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be996-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be996-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be996-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be996-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be996-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be996-120">See Also</span></span>  
 [<span data-ttu-id="be996-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="be996-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="be996-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="be996-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="be996-123">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="be996-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
