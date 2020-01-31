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
ms.openlocfilehash: e77344a99189ec8e234129262d45698c794dc249
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788513"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="44894-102">Metoda ICorDebugILFrame4::GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="44894-102">ICorDebugILFrame4::GetCodeEx Method</span></span>
<span data-ttu-id="44894-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="44894-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="44894-104">Pobiera wskaźnik do kodu, który jest wykonywany przez tę ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="44894-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44894-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="44894-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44894-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="44894-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="44894-107">podczas Element członkowski wyliczenia [ILCodeKind](ilcodekind-enumeration.md) , który określa, czy język pośredni (IL) zdefiniowany przez żądanie ReJIT profilera zostanie uwzględniony w ramce.</span><span class="sxs-lookup"><span data-stu-id="44894-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="44894-108">określoną Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje kod, który jest wykonywany przez tę ramkę stosu.</span><span class="sxs-lookup"><span data-stu-id="44894-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44894-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44894-109">Remarks</span></span>  
 <span data-ttu-id="44894-110">Ta metoda jest podobna do metody [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) , z tą różnicą, że opcjonalnie uzyskuje dostęp do kodu zdefiniowanego przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="44894-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="44894-111">Wywołanie tej metody z `flags` wartością `ILCODE_ORIGINAL_IL` jest równoważne wywołaniu metody [GetCode](icordebugframe-getcode-method.md); Jeśli metoda jest Instrumentacją, jej kod IL nie będzie dostępny.</span><span class="sxs-lookup"><span data-stu-id="44894-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="44894-112">`ILCODE_REJIT_IL` zezwala debugerowi na dostęp do IL zdefiniowanego przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="44894-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="44894-113">Jeśli IL nie ma instrumentacji, `ppCode` ma **wartość null**, a metoda zwraca `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="44894-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44894-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44894-114">Requirements</span></span>  
 <span data-ttu-id="44894-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44894-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44894-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="44894-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44894-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="44894-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44894-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44894-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44894-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44894-119">See also</span></span>

- [<span data-ttu-id="44894-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="44894-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="44894-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="44894-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="44894-122">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="44894-122">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
