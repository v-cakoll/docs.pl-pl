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
ms.openlocfilehash: 8826644ae3bdfbef76e9143de5f8f449c1555095
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761204"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="3ecfb-102">ICorDebugManagedCallback::UnloadModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ecfb-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="3ecfb-103">Powiadamia debuger wspólnej moduł środowiska uruchomieniowego języka (DLL) został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="3ecfb-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ecfb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ecfb-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ecfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ecfb-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="3ecfb-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, który zawierał moduł.</span><span class="sxs-lookup"><span data-stu-id="3ecfb-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="3ecfb-107">[in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje modułu.</span><span class="sxs-lookup"><span data-stu-id="3ecfb-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ecfb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ecfb-108">Remarks</span></span>  
 <span data-ttu-id="3ecfb-109">Nie można używać modułu po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="3ecfb-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ecfb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ecfb-110">Requirements</span></span>  
 <span data-ttu-id="3ecfb-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ecfb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ecfb-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ecfb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ecfb-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ecfb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ecfb-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ecfb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ecfb-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ecfb-115">See also</span></span>

- [<span data-ttu-id="3ecfb-116">LoadModule, metoda</span><span class="sxs-lookup"><span data-stu-id="3ecfb-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="3ecfb-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ecfb-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
