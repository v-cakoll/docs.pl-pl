---
title: "ICorDebug::Terminate — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e416f8ea20bde49a1c1cdb5d61bc4a6bfbce7913
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="ca4df-102">ICorDebug::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="ca4df-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="ca4df-103">Kończy `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ca4df-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca4df-104">`Terminate`Nie można wywołać, dopóki [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) Odebrano wywołania zwrotnego dla wszystkich procesów debugowany.</span><span class="sxs-lookup"><span data-stu-id="ca4df-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4df-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca4df-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ca4df-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca4df-106">Remarks</span></span>  
 <span data-ttu-id="ca4df-107">`Terminate`musi być wywoływane, gdy `ICorDebug` obiektu nie jest już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="ca4df-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca4df-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca4df-108">Requirements</span></span>  
 <span data-ttu-id="ca4df-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca4df-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca4df-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca4df-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca4df-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca4df-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca4df-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca4df-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4df-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca4df-113">See Also</span></span>  
 [<span data-ttu-id="ca4df-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca4df-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
