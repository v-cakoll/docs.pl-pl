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
ms.openlocfilehash: 9a74fd64e046ab3a8943e9a975e4de808c662677
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090957"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="8cff3-102">Metoda ICorDebugILFrame4::GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="8cff3-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="8cff3-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="8cff3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8cff3-104">Pobiera wskaźnik do kodu, który jest wykonywany przez tę ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="8cff3-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cff3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cff3-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cff3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cff3-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="8cff3-107">podczas Element członkowski wyliczenia [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) , który określa, czy język pośredni (IL) zdefiniowany przez żądanie ReJIT profilera zostanie uwzględniony w ramce.</span><span class="sxs-lookup"><span data-stu-id="8cff3-107">[in] An [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="8cff3-108">określoną Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który jest wykonywany przez tę ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="8cff3-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cff3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cff3-109">Remarks</span></span>  
 <span data-ttu-id="8cff3-110">Ta metoda jest podobna do metody [ICorDebugFrame:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do kodu zdefiniowanego przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="8cff3-110">This method is similar to the [ICorDebugFrame::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="8cff3-111">Wywołanie tej metody z `flags` wartością `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu metody [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); Jeśli metoda jest Instrumentacją, jej kod IL nie będzie dostępny.</span><span class="sxs-lookup"><span data-stu-id="8cff3-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="8cff3-112">`ILCODE_REJIT_IL` zezwala debugerowi na dostęp do IL zdefiniowanego przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="8cff3-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="8cff3-113">Jeśli IL nie ma instrumentacji, `ppCode` ma **wartość null**, a metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="8cff3-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cff3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cff3-114">Requirements</span></span>  
 <span data-ttu-id="8cff3-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cff3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cff3-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8cff3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cff3-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8cff3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cff3-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cff3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cff3-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cff3-119">See also</span></span>

- [<span data-ttu-id="8cff3-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="8cff3-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="8cff3-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8cff3-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8cff3-122">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="8cff3-122">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
