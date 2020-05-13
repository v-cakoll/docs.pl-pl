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
ms.openlocfilehash: 8d6ef550309ea7f8bae616a5f7e5c41b4f07374a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213728"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="62e25-102">Metoda ICorDebugILFrame4::GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="62e25-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="62e25-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="62e25-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="62e25-104">Pobiera wartość określonej zmiennej lokalnej w ramce stosu języka pośredniego (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodanej w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="62e25-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e25-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e25-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62e25-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="62e25-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="62e25-107">podczas Element członkowski wyliczenia [ILCodeKind](ilcodekind-enumeration.md) , który określa, czy zmienna dodana w Instrumentacji ReJIT profilera jest uwzględniona w ramce.</span><span class="sxs-lookup"><span data-stu-id="62e25-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="62e25-108">podczas Indeks zmiennej lokalnej w ramce stosu IL.</span><span class="sxs-lookup"><span data-stu-id="62e25-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="62e25-109">określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="62e25-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62e25-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62e25-110">Remarks</span></span>  
 <span data-ttu-id="62e25-111">Ta metoda jest podobna do metody [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennej dodanej w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="62e25-111">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="62e25-112">Wywołanie tej metody z `flags` wartością `ILCODE_ORIGINAL_IL` jest równoznaczne z wywołaniem metody [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md); Jeśli metoda jest Instrumentacją przy użyciu dodatkowych zmiennych lokalnych, nie można uzyskać dostępu do tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="62e25-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="62e25-113">`ILCODE_REJIT_IL`zezwala debugerowi na dostęp do zmiennych lokalnych dodanych w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="62e25-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="62e25-114">Jeśli IL nie jest Instrumentacją, metoda zwraca `E_INVALIDARG` .</span><span class="sxs-lookup"><span data-stu-id="62e25-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e25-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62e25-115">Requirements</span></span>  
 <span data-ttu-id="62e25-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62e25-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62e25-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="62e25-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62e25-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="62e25-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62e25-119">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62e25-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e25-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e25-120">See also</span></span>

- [<span data-ttu-id="62e25-121">Interfejs ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="62e25-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="62e25-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="62e25-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="62e25-123">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="62e25-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
