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
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178791"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="858f9-102">Metoda ICorDebugILFrame4::GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="858f9-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="858f9-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="858f9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="858f9-104">Pobiera wskaźnik do kodu, który wykonuje tę ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="858f9-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="858f9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="858f9-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="858f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="858f9-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="858f9-107">[w] Element członkowski wyliczania [ILCodeKind,](ilcodekind-enumeration.md) który określa, czy język pośredni (IL) zdefiniowany przez żądanie ReJIT profilera znajduje się w ramce.</span><span class="sxs-lookup"><span data-stu-id="858f9-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="858f9-108">[na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który wykonuje tę ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="858f9-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="858f9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="858f9-109">Remarks</span></span>  
 <span data-ttu-id="858f9-110">Ta metoda jest podobna do [metody ICorDebugFrame::GetCode,](icordebugframe-getcode-method.md) z tą różnicą, że opcjonalnie uzyskuje dostęp do kodu zdefiniowanego przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="858f9-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="858f9-111">Wywołanie tej `flags` metody `ILCODE_ORIGINAL_IL` o wartości jest równoważne wywołaniu [GetCode;](icordebugframe-getcode-method.md) jeśli metoda jest oprzyrządowana, jej IL nie będzie dostępny.</span><span class="sxs-lookup"><span data-stu-id="858f9-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="858f9-112">`ILCODE_REJIT_IL`umożliwia debugerowi dostęp do identyfikatora IL zdefiniowanego przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="858f9-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="858f9-113">Jeśli IL nie jest `ppCode` instrumentowany, ma wartość `S_OK` **null**, a metoda zwraca .</span><span class="sxs-lookup"><span data-stu-id="858f9-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="858f9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="858f9-114">Requirements</span></span>  
 <span data-ttu-id="858f9-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="858f9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="858f9-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="858f9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="858f9-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="858f9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="858f9-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="858f9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="858f9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="858f9-119">See also</span></span>

- [<span data-ttu-id="858f9-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="858f9-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="858f9-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="858f9-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="858f9-122">ReJIT: Poradnik</span><span class="sxs-lookup"><span data-stu-id="858f9-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
