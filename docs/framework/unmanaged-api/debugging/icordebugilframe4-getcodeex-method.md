---
title: Metoda ICorDebugILFrame4::GetCodeEx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e5d1d480014e90d3fea9790b10e0dace5a0847ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="00192-102">Metoda ICorDebugILFrame4::GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="00192-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="00192-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="00192-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="00192-104">Pobiera wskaźnik do kodu, który jest wykonywany tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="00192-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00192-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="00192-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00192-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="00192-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="00192-107">[in] [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) element członkowski wyliczenia, która określa, czy język pośredni (IL), zdefiniowany przez profiler ReJIT żądanie znajduje się w ramce.</span><span class="sxs-lookup"><span data-stu-id="00192-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="00192-108">[out] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który jest wykonywany tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="00192-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00192-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00192-109">Remarks</span></span>  
 <span data-ttu-id="00192-110">Ta metoda jest podobna do [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) metody, z wyjątkiem, że opcjonalnie dostęp do kodu określonego przez profiler ReJIT żądanie.</span><span class="sxs-lookup"><span data-stu-id="00192-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="00192-111">Wywołanie tej metody za pomocą `flags` wartość `ILCODE_ORIGINAL_IL` jest odpowiednikiem wywołania [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); w wypadku metody został zinstrumentowany, jego IL nie będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="00192-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="00192-112">`ILCODE_REJIT_IL`Umożliwia debugera IL zdefiniowany przez profiler ReJIT żądanie dostępu do.</span><span class="sxs-lookup"><span data-stu-id="00192-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="00192-113">Jeśli nie ma instrumentacji IL, `ppCode` jest **null**, a metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="00192-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00192-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00192-114">Requirements</span></span>  
 <span data-ttu-id="00192-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00192-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00192-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00192-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00192-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00192-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00192-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00192-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00192-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00192-119">See Also</span></span>  
 [<span data-ttu-id="00192-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="00192-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [<span data-ttu-id="00192-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="00192-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="00192-122">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="00192-122">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
