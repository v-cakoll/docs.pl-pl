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
ms.openlocfilehash: eb4eaaa23a810a23852dc5ef88d61c6a5d0f0ccd
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926806"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="e66dd-102">Metoda ICorDebugILFrame4::GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="e66dd-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="e66dd-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="e66dd-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e66dd-104">Pobiera wartość określonej zmiennej lokalnej w ramce stosu języka pośredniego (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodanej w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="e66dd-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66dd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e66dd-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e66dd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e66dd-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="e66dd-107">podczas Element członkowski wyliczenia [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , który określa, czy zmienna dodana w Instrumentacji ReJIT profilera jest uwzględniona w ramce.</span><span class="sxs-lookup"><span data-stu-id="e66dd-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="e66dd-108">podczas Indeks zmiennej lokalnej w ramce stosu IL.</span><span class="sxs-lookup"><span data-stu-id="e66dd-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e66dd-109">określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="e66dd-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e66dd-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e66dd-110">Remarks</span></span>  
 <span data-ttu-id="e66dd-111">Ta metoda jest podobna do metody [GetLocalVariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennej dodanej w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="e66dd-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="e66dd-112">Wywołanie tej metody z `flags` `ILCODE_ORIGINAL_IL` wartością jest równoznaczne z wywołaniem metody [GetLocalVariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Jeśli metoda jest Instrumentacją przy użyciu dodatkowych zmiennych lokalnych, nie można uzyskać dostępu do tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e66dd-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="e66dd-113">`ILCODE_REJIT_IL`zezwala debugerowi na dostęp do zmiennych lokalnych dodanych w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="e66dd-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="e66dd-114">Jeśli IL nie jest Instrumentacją, metoda zwraca `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="e66dd-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e66dd-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e66dd-115">Requirements</span></span>  
 <span data-ttu-id="e66dd-116">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e66dd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e66dd-117">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e66dd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e66dd-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e66dd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e66dd-119">**.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e66dd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66dd-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e66dd-120">See also</span></span>

- [<span data-ttu-id="e66dd-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="e66dd-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="e66dd-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e66dd-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e66dd-123">ReJIT: Przewodnik krok po kroku</span><span class="sxs-lookup"><span data-stu-id="e66dd-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
