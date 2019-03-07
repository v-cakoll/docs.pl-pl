---
title: ICorDebugFunctionBreakpoint::GetFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1da93ea073d6ae9f2e79f251014b2db5282a22c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496017"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="69aa9-102">ICorDebugFunctionBreakpoint::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="69aa9-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="69aa9-103">Pobiera wskaźnik interfejsu do ICorDebugFunction, który odwołuje się do funkcji, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="69aa9-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69aa9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69aa9-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69aa9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69aa9-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="69aa9-106">[out] Wskaźnik do adresu funkcji, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="69aa9-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69aa9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69aa9-107">Requirements</span></span>  
 <span data-ttu-id="69aa9-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69aa9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69aa9-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69aa9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69aa9-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69aa9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69aa9-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69aa9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
