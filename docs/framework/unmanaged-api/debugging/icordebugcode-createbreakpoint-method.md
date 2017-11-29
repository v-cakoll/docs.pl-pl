---
title: "ICorDebugCode::CreateBreakpoint — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.CreateBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 214d032129613230b8c55cdd286ea637227a626e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="e3c5e-102">ICorDebugCode::CreateBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3c5e-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="e3c5e-103">Tworzy punkt przerwania w tym segmencie kodu od wskazanego przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="e3c5e-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3c5e-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3c5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3c5e-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="e3c5e-106">[in] Przesunięcie, w którym chcesz utworzyć punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="e3c5e-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="e3c5e-107">[out] Wskaźnik do obiektu "ICorDebugFunctionBreakpoint", który reprezentuje punkt przerwania adresu.</span><span class="sxs-lookup"><span data-stu-id="e3c5e-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3c5e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3c5e-108">Remarks</span></span>  
 <span data-ttu-id="e3c5e-109">Aby punkt przerwania jest aktywna, można dodać go do obiektu procesu.</span><span class="sxs-lookup"><span data-stu-id="e3c5e-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="e3c5e-110">Jeśli ten kod jest kod języka pośredniego (MSIL) firmy Microsoft, a istnieje just-in-time (JIT)-skompilowanych wersji natywnego kodu punkt przerwania zostaną zastosowane w również JIT skompilowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="e3c5e-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="e3c5e-111">(Taki sam jest wartość true, jeśli kod jest kompilacji JIT później).</span><span class="sxs-lookup"><span data-stu-id="e3c5e-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c5e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3c5e-112">Requirements</span></span>  
 <span data-ttu-id="e3c5e-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c5e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c5e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3c5e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3c5e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3c5e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3c5e-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c5e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c5e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3c5e-117">See Also</span></span>  
 
