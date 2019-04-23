---
title: ICorDebug::Terminate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 321298ce942b35d11a861c87cdf6b8714179ea97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080842"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="d9d4d-102">ICorDebug::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9d4d-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="d9d4d-103">Kończy `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9d4d-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9d4d-104">`Terminate` nie powinien być wywoływany do momentu [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) otrzymał wywołania zwrotnego dla wszystkich procesów debugowania.</span><span class="sxs-lookup"><span data-stu-id="d9d4d-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d4d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9d4d-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d9d4d-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9d4d-106">Remarks</span></span>  
 <span data-ttu-id="d9d4d-107">`Terminate` musi być wywoływana, gdy `ICorDebug` obiektu nie jest już potrzebny.</span><span class="sxs-lookup"><span data-stu-id="d9d4d-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d4d-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9d4d-108">Requirements</span></span>  
 <span data-ttu-id="d9d4d-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9d4d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d4d-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9d4d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9d4d-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9d4d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9d4d-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d4d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d4d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9d4d-113">See also</span></span>

- [<span data-ttu-id="d9d4d-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9d4d-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
