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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 728b9fd287a23fd1933032906ff6a47b35285b4b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764041"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="3d95e-102">ICorDebugModuleBreakpoint::GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d95e-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="3d95e-103">Pobiera wskaźnik interfejsu do "ICorDebugModule", który odwołuje się moduł, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="3d95e-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d95e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d95e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d95e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d95e-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="3d95e-106">[out] Wskaźnik na adres `ICorDebugModule` interfejsu, który odwołuje się moduł, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="3d95e-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d95e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d95e-107">Requirements</span></span>  
 <span data-ttu-id="3d95e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d95e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d95e-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d95e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d95e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d95e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d95e-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d95e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d95e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d95e-112">See also</span></span>
