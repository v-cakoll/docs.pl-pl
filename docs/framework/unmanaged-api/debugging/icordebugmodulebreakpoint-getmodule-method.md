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
ms.openlocfilehash: 5cbb1aa9c81101eb818a9e7829c777efd3923b5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="ee263-102">ICorDebugModuleBreakpoint::GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="ee263-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="ee263-103">Pobiera wskaźnika interfejsu do "ICorDebugModule", który odwołuje się do modułu, w którym ten punkt przerwania jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="ee263-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee263-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee263-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee263-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee263-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="ee263-106">[out] Wskaźnik do adresu `ICorDebugModule` interfejsu, który odwołuje się do modułu, w której zostanie ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="ee263-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee263-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee263-107">Requirements</span></span>  
 <span data-ttu-id="ee263-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee263-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee263-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee263-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee263-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee263-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee263-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee263-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee263-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee263-112">See Also</span></span>  
 
