---
title: ICorDebugModuleBreakpoint::GetModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint::GetModule
helpviewer_keywords:
- ICorDebugModuleBreakpoint::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: ffd5d9ec-4564-4200-b625-b306eec0ebd7
topic_type:
- apiref
ms.openlocfilehash: 714819504099ea978ed31d471b4ceb9fc17a6552
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212298"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="caa6f-102">ICorDebugModuleBreakpoint::GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="caa6f-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="caa6f-103">Pobiera wskaźnik interfejsu do "ICorDebugModule", który odwołuje się do modułu, w którym jest ustawiony ten punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="caa6f-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa6f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="caa6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caa6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="caa6f-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="caa6f-106">określoną Wskaźnik do adresu `ICorDebugModule` interfejsu, który odwołuje się do modułu, w którym jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="caa6f-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa6f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="caa6f-107">Requirements</span></span>  
 <span data-ttu-id="caa6f-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa6f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa6f-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="caa6f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="caa6f-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="caa6f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="caa6f-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa6f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa6f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="caa6f-112">See also</span></span>
