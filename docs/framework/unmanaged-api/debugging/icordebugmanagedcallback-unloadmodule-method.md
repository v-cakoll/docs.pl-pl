---
title: ICorDebugManagedCallback::UnloadModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10f2b65b65a5e15239f731ddcb471ee7548e1631
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638067"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="94f0b-102">ICorDebugManagedCallback::UnloadModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="94f0b-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="94f0b-103">Powiadamia debuger wspólnej moduł środowiska uruchomieniowego języka (DLL) został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="94f0b-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94f0b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94f0b-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94f0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94f0b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="94f0b-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, który zawierał moduł.</span><span class="sxs-lookup"><span data-stu-id="94f0b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="94f0b-107">[in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje modułu.</span><span class="sxs-lookup"><span data-stu-id="94f0b-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94f0b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94f0b-108">Remarks</span></span>  
 <span data-ttu-id="94f0b-109">Nie można używać modułu po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="94f0b-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94f0b-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94f0b-110">Requirements</span></span>  
 <span data-ttu-id="94f0b-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94f0b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94f0b-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94f0b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94f0b-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94f0b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94f0b-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94f0b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94f0b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94f0b-115">See also</span></span>
- [<span data-ttu-id="94f0b-116">LoadModule, metoda</span><span class="sxs-lookup"><span data-stu-id="94f0b-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="94f0b-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="94f0b-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
