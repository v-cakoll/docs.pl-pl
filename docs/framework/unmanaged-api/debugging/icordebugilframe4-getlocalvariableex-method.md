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
ms.openlocfilehash: 017c14e9170087f3c3c9de64f50d165fc91aa297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782417"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="bbfba-102">Metoda ICorDebugILFrame4::GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="bbfba-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="bbfba-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="bbfba-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="bbfba-104">Pobiera wartość określonej zmiennej lokalnej w ramce stosu języka pośredniego (IL) i opcjonalnie uzyskuje dostęp do zmiennej dodanej w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="bbfba-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfba-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbfba-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbfba-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbfba-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="bbfba-107">podczas Element członkowski wyliczenia [ILCodeKind](ilcodekind-enumeration.md) , który określa, czy zmienna dodana w Instrumentacji ReJIT profilera jest uwzględniona w ramce.</span><span class="sxs-lookup"><span data-stu-id="bbfba-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="bbfba-108">podczas Indeks zmiennej lokalnej w ramce stosu IL.</span><span class="sxs-lookup"><span data-stu-id="bbfba-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="bbfba-109">określoną Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="bbfba-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbfba-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbfba-110">Remarks</span></span>  
 <span data-ttu-id="bbfba-111">Ta metoda jest podobna do metody [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do zmiennej dodanej w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="bbfba-111">This method is similar to the [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="bbfba-112">Wywołanie tej metody z `flags` wartością `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md); Jeśli metoda jest Instrumentacją z dodatkowymi zmiennymi lokalnymi, nie można uzyskać dostępu do tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="bbfba-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="bbfba-113">`ILCODE_REJIT_IL` pozwala debugerowi na dostęp do zmiennych lokalnych dodanych w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="bbfba-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="bbfba-114">Jeśli IL nie jest Instrumentacją, metoda zwraca `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="bbfba-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfba-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbfba-115">Requirements</span></span>  
 <span data-ttu-id="bbfba-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbfba-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbfba-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bbfba-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbfba-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bbfba-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbfba-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbfba-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfba-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbfba-120">See also</span></span>

- [<span data-ttu-id="bbfba-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="bbfba-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="bbfba-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bbfba-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bbfba-123">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="bbfba-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
