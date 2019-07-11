---
title: ICorDebugFunctionBreakpoint::GetOffset — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67e71002a78023ad6e8ef89c7a57d484a65aaeb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756383"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="58ec8-102">ICorDebugFunctionBreakpoint::GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="58ec8-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="58ec8-103">Pobiera przesunięcie punktu przerwania w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="58ec8-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ec8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58ec8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58ec8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58ec8-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="58ec8-106">[out] Wskaźnik do przesunięcie punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="58ec8-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ec8-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58ec8-107">Requirements</span></span>  
 <span data-ttu-id="58ec8-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ec8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ec8-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58ec8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58ec8-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58ec8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ec8-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ec8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
