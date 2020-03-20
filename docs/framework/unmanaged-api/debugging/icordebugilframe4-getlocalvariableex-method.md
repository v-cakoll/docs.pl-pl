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
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178775"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="838d4-102">Metoda ICorDebugILFrame4::GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="838d4-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="838d4-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="838d4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="838d4-104">Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu języka pośredniego (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodanej w instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="838d4-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="838d4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="838d4-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="838d4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="838d4-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="838d4-107">[w] Element członkowski wyliczenia [ILCodeKind,](ilcodekind-enumeration.md) który określa, czy zmienna dodana w instrumentacji ReJIT profilera jest zawarta w ramce.</span><span class="sxs-lookup"><span data-stu-id="838d4-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="838d4-108">[w] Indeks zmiennej lokalnej w ramce stosu IL.</span><span class="sxs-lookup"><span data-stu-id="838d4-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="838d4-109">[na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="838d4-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="838d4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="838d4-110">Remarks</span></span>  
 <span data-ttu-id="838d4-111">Ta metoda jest podobna do [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) metody, z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennej dodanej w profiler Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="838d4-111">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="838d4-112">Wywołanie tej `flags` metody `ILCODE_ORIGINAL_IL` o wartości jest równoznaczne z wywołaniem [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); jeśli metoda jest instrumentowana z dodatkowymi zmiennymi lokalnymi, nie można uzyskać dostępu do tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="838d4-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="838d4-113">`ILCODE_REJIT_IL`umożliwia debugerowi dostęp do zmiennych lokalnych dodanych w instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="838d4-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="838d4-114">Jeśli IL nie jest instrumentowany, `E_INVALIDARG`metoda zwraca .</span><span class="sxs-lookup"><span data-stu-id="838d4-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="838d4-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="838d4-115">Requirements</span></span>  
 <span data-ttu-id="838d4-116">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="838d4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="838d4-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="838d4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="838d4-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="838d4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="838d4-119">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="838d4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838d4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="838d4-120">See also</span></span>

- [<span data-ttu-id="838d4-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="838d4-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="838d4-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="838d4-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="838d4-123">ReJIT: Poradnik</span><span class="sxs-lookup"><span data-stu-id="838d4-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
