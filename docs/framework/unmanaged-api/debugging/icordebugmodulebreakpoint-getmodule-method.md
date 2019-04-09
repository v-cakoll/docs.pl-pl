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
ms.openlocfilehash: 51403c52d7f8a216e83b817f157979f4af1c433a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162871"
---
# <a name="icordebugmodulebreakpointgetmodule-method"></a><span data-ttu-id="0218d-102">ICorDebugModuleBreakpoint::GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="0218d-102">ICorDebugModuleBreakpoint::GetModule Method</span></span>
<span data-ttu-id="0218d-103">Pobiera wskaźnik interfejsu do "ICorDebugModule", który odwołuje się moduł, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="0218d-103">Gets an interface pointer to an "ICorDebugModule" that references the module in which this breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0218d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0218d-104">Syntax</span></span>  
  
```  
HRESULT GetModule (  
    [out] ICorDebugModule   **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0218d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0218d-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="0218d-106">[out] Wskaźnik na adres `ICorDebugModule` interfejsu, który odwołuje się moduł, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="0218d-106">[out] A pointer to the address of an `ICorDebugModule` interface that references the module in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0218d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0218d-107">Requirements</span></span>  
 <span data-ttu-id="0218d-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0218d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0218d-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0218d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0218d-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0218d-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0218d-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0218d-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0218d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0218d-112">See also</span></span>
