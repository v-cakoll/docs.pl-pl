---
title: "ICorDebugFunctionBreakpoint::GetOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ca890b20451b0fab6145d8b8577f705bf3fa3202
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="5e727-102">ICorDebugFunctionBreakpoint::GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e727-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="5e727-103">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e727-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e727-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e727-104">Syntax</span></span>  
  
```  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e727-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e727-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="5e727-106">[out] Wskaźnik do przesunięcie punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="5e727-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e727-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e727-107">Requirements</span></span>  
 <span data-ttu-id="5e727-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e727-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e727-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e727-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e727-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e727-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e727-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e727-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
