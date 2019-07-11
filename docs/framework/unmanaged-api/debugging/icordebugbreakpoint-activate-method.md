---
title: ICorDebugBreakpoint::Activate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f056e4ae233e70223755c1961cd3ee5da68ec90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745178"
---
# <a name="icordebugbreakpointactivate-method"></a><span data-ttu-id="7a3d6-102">ICorDebugBreakpoint::Activate — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a3d6-102">ICorDebugBreakpoint::Activate Method</span></span>
<span data-ttu-id="7a3d6-103">Ustawia stan aktywny `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-103">Sets the active state of this `ICorDebugBreakpoint`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a3d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a3d6-104">Syntax</span></span>  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a3d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a3d6-105">Parameters</span></span>  
 `bActive`  
 <span data-ttu-id="7a3d6-106">[in] Ustaw tę wartość na `true` do określenia stanu jako aktywny; w przeciwnym wypadku ustaw tę wartość na `false`.</span><span class="sxs-lookup"><span data-stu-id="7a3d6-106">[in] Set this value to `true` to specify the state as active; otherwise, set this value to `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a3d6-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a3d6-107">Requirements</span></span>  
 <span data-ttu-id="7a3d6-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a3d6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3d6-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a3d6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a3d6-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a3d6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a3d6-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3d6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
