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
ms.openlocfilehash: a64df9f821021547efd08045e9f67fee25173e5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137439"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="73ff4-102">ICorDebugManagedCallback2::DestroyConnection — Metoda</span><span class="sxs-lookup"><span data-stu-id="73ff4-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>
<span data-ttu-id="73ff4-103">Powiadamia debuger o przerwaniu określonego połączenia.</span><span class="sxs-lookup"><span data-stu-id="73ff4-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ff4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73ff4-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73ff4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73ff4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="73ff4-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces zawierający zniszczone połączenie.</span><span class="sxs-lookup"><span data-stu-id="73ff4-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="73ff4-107">podczas Identyfikator zerwanego połączenia.</span><span class="sxs-lookup"><span data-stu-id="73ff4-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73ff4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73ff4-108">Remarks</span></span>  
 <span data-ttu-id="73ff4-109">Wywołanie zwrotne `DestroyConnection` zostanie wyzwolone, gdy host wywoła [ICLRDebugManager:: EndConnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) w [interfejsie API hostingu](../../../../docs/framework/unmanaged-api/hosting/index.md).</span><span class="sxs-lookup"><span data-stu-id="73ff4-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73ff4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73ff4-110">Requirements</span></span>  
 <span data-ttu-id="73ff4-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73ff4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73ff4-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73ff4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73ff4-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73ff4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73ff4-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73ff4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ff4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73ff4-115">See also</span></span>

- [<span data-ttu-id="73ff4-116">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="73ff4-116">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="73ff4-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="73ff4-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
