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
ms.openlocfilehash: 0f6fe5d7eb5926d48809bb6490ba75df9d4a5033
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213156"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="ec8b7-102">ICorDebugFunctionBreakpoint::GetOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec8b7-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="ec8b7-103">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="ec8b7-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec8b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec8b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec8b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec8b7-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="ec8b7-106">określoną Wskaźnik do przesunięcia punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="ec8b7-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec8b7-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec8b7-107">Requirements</span></span>  
 <span data-ttu-id="ec8b7-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec8b7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec8b7-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec8b7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec8b7-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ec8b7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec8b7-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec8b7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
