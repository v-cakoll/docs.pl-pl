---
title: ICorDebugManagedCallback2::DestroyConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35ae3a9761798ed9ea42b984f2c6c2cad4e42777
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075928"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="d9950-102">ICorDebugManagedCallback2::DestroyConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9950-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="d9950-103">Powiadamia debugera, że określone połączenie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="d9950-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9950-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9950-104">Syntax</span></span>  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9950-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9950-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d9950-106">[in] Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces zawierający połączenia, która została zniszczona.</span><span class="sxs-lookup"><span data-stu-id="d9950-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="d9950-107">[in] Identyfikator połączenia, która została zniszczona.</span><span class="sxs-lookup"><span data-stu-id="d9950-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9950-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9950-108">Remarks</span></span>  
 <span data-ttu-id="d9950-109">A `DestroyConnection` wywołania zwrotnego zostanie wyzwolone, gdy host wywołuje [iclrdebugmanager::endconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) w [interfejs API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9950-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9950-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9950-110">Requirements</span></span>  
 <span data-ttu-id="d9950-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9950-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9950-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9950-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9950-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9950-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d9950-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d9950-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d9950-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9950-115">See also</span></span>

- [<span data-ttu-id="d9950-116">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d9950-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d9950-117">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d9950-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
