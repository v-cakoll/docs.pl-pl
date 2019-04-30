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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763792"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="d0fb3-102">ICorDebugFunctionBreakpoint::GetFunction — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0fb3-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="d0fb3-103">Pobiera wskaźnik interfejsu do ICorDebugFunction, który odwołuje się do funkcji, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="d0fb3-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0fb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0fb3-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0fb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0fb3-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="d0fb3-106">[out] Wskaźnik do adresu funkcji, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="d0fb3-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0fb3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0fb3-107">Requirements</span></span>  
 <span data-ttu-id="d0fb3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0fb3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0fb3-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0fb3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0fb3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0fb3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0fb3-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0fb3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
