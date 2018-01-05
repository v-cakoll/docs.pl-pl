---
title: "ICorDebugBreakpoint::IsActive — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394caaaff0b0269acd63a590225ffde420ebfd2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="33fd0-102">ICorDebugBreakpoint::IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="33fd0-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="33fd0-103">Pobiera wartość wskazującą, czy to `ICorDebugBreakpoint` jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="33fd0-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33fd0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33fd0-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33fd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33fd0-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="33fd0-106">[out] `true` Jeśli ten punkt przerwania jest aktywne, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="33fd0-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33fd0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33fd0-107">Requirements</span></span>  
 <span data-ttu-id="33fd0-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33fd0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33fd0-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33fd0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33fd0-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33fd0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33fd0-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33fd0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
