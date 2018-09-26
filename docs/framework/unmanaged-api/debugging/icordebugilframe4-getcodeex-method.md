---
title: Metoda ICorDebugILFrame4::GetCodeEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24be4507e8ad6cde1e9c50582e352f0fc9b12ed3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47110973"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="fe9f5-102">Metoda ICorDebugILFrame4::GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="fe9f5-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="fe9f5-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="fe9f5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fe9f5-104">Pobiera wskaźnik do kodu, który jest wykonywany tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe9f5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe9f5-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe9f5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe9f5-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="fe9f5-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) składowej wyliczenia, która określa, czy języka pośredniego (IL), zdefiniowane przez żądanie ReJIT programu profilującego znajduje się w ramce.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="fe9f5-108">[out] Wskaźnik do adresu obiektu "ICorDebugCode", która przedstawia kod, który wykonuje tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe9f5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe9f5-109">Remarks</span></span>  
 <span data-ttu-id="fe9f5-110">Ta metoda jest podobna do [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, z wyjątkiem tego opcjonalnie uzyskuje dostęp kod zdefiniowany przez żądanie ReJIT programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="fe9f5-111">Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest równoważne z wywoływaniem [getcode —](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Jeśli został zinstrumentowany na metodzie, jej IL nie będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="fe9f5-112">`ILCODE_REJIT_IL` Umożliwia debugera dostępu IL określone przez żądanie ReJIT programu profilującego do.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="fe9f5-113">Jeśli nie ma instrumentacji IL, `ppCode` jest **null**, a metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe9f5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe9f5-114">Requirements</span></span>  
 <span data-ttu-id="fe9f5-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe9f5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe9f5-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe9f5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe9f5-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe9f5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe9f5-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe9f5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9f5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe9f5-119">See Also</span></span>  
 [<span data-ttu-id="fe9f5-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe9f5-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="fe9f5-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fe9f5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fe9f5-122">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="fe9f5-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
