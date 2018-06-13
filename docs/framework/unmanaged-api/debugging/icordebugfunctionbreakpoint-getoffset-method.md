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
ms.openlocfilehash: aca1d77ace512ca84cda3b6844d214e4c8d6cad7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412068"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="21cb4-102">ICorDebugFunctionBreakpoint::GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="21cb4-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="21cb4-103">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="21cb4-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21cb4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21cb4-104">Syntax</span></span>  
  
```  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21cb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21cb4-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="21cb4-106">[out] Wskaźnik do przesunięcie punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="21cb4-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21cb4-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21cb4-107">Requirements</span></span>  
 <span data-ttu-id="21cb4-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21cb4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21cb4-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21cb4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21cb4-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21cb4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21cb4-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21cb4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
