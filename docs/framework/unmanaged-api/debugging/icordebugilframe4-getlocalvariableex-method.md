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
ms.openlocfilehash: 18a6154ad3fe3ee384a38007ab371e83482193ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545978"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a><span data-ttu-id="cb9f6-102">Metoda ICorDebugILFrame4::GetLocalVariableEx</span><span class="sxs-lookup"><span data-stu-id="cb9f6-102">ICorDebugILFrame4::GetLocalVariableEx Method</span></span>
<span data-ttu-id="cb9f6-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="cb9f6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cb9f6-104">Pobiera wartość określonej zmiennej lokalnej w tej ramce stosu języka pośredniego (IL), a opcjonalnie uzyskuje dostęp do zmiennej dodane w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-104">Gets the value of the specified local variable in this intermediate language (IL) stack frame, and optionally accesses a variable added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb9f6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb9f6-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb9f6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb9f6-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="cb9f6-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) składowej wyliczenia, która określa, czy zmienna dodany do programu profilującego Instrumentację ReJIT znajduje się w ramce.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether a variable added in profiler ReJIT instrumentation is included in the frame.</span></span>  
  
 `dwIndex`  
 <span data-ttu-id="cb9f6-108">[in] Indeks zmiennej lokalnej w ramce stosu IL.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-108">[in] The index of the local variable in the IL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="cb9f6-109">[out] Wskaźnik na adres "ICorDebugValue" obiekt, który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-109">[out] A pointer to the address of an "ICorDebugValue" object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb9f6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb9f6-110">Remarks</span></span>  
 <span data-ttu-id="cb9f6-111">Ta metoda jest podobna do [getlocalvariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody, z wyjątkiem tego opcjonalnie uzyskuje dostęp zmienną dodane w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-111">This method is similar to the [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) method, except that it optionally accesses a variable added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="cb9f6-112">Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest równoważne z wywoływaniem [getlocalvariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); Jeśli metoda jest wyposażone w dodatkowe zmienne lokalne, nie można uzyskać dostępu do tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); if the method is instrumented with additional local variables, those variables cannot be accessed.</span></span> <span data-ttu-id="cb9f6-113">`ILCODE_REJIT_IL` Pozwala debugerowi, aby uzyskać dostęp do zmiennych lokalnych, dodane w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-113">`ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="cb9f6-114">Jeśli nie ma instrumentacji IL, metoda zwraca `E_INVALIDARG`.</span><span class="sxs-lookup"><span data-stu-id="cb9f6-114">If the IL is not instrumented, the method returns `E_INVALIDARG`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb9f6-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb9f6-115">Requirements</span></span>  
 <span data-ttu-id="cb9f6-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb9f6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb9f6-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb9f6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb9f6-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb9f6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb9f6-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb9f6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9f6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb9f6-120">See also</span></span>
- [<span data-ttu-id="cb9f6-121">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb9f6-121">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="cb9f6-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cb9f6-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cb9f6-123">ReJIT: Przewodniku z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="cb9f6-123">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
