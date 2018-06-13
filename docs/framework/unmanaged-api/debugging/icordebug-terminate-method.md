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
ms.openlocfilehash: 2c2b590e7402bf29ffeb5bd14fc383edae41a04e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404004"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="d29d0-102">ICorDebug::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="d29d0-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="d29d0-103">Kończy `ICorDebug` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d29d0-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d29d0-104">`Terminate` Nie można wywołać, dopóki [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) Odebrano wywołania zwrotnego dla wszystkich procesów debugowany.</span><span class="sxs-lookup"><span data-stu-id="d29d0-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d29d0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d29d0-105">Syntax</span></span>  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d29d0-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d29d0-106">Remarks</span></span>  
 <span data-ttu-id="d29d0-107">`Terminate` musi być wywoływane, gdy `ICorDebug` obiektu nie jest już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="d29d0-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d29d0-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d29d0-108">Requirements</span></span>  
 <span data-ttu-id="d29d0-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d29d0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d29d0-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d29d0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d29d0-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d29d0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d29d0-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d29d0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d29d0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d29d0-113">See Also</span></span>  
 [<span data-ttu-id="d29d0-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="d29d0-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
