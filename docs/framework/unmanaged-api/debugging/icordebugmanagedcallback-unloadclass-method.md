---
title: ICorDebugManagedCallback::UnloadClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3eb8bf59ee2a91c62a6ff74b1903d92607a9ffe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197877"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="86a89-102">ICorDebugManagedCallback::UnloadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="86a89-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="86a89-103">Powiadamia debuger jest zwalniany klasy.</span><span class="sxs-lookup"><span data-stu-id="86a89-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86a89-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86a89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86a89-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="86a89-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji z klasą.</span><span class="sxs-lookup"><span data-stu-id="86a89-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="86a89-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="86a89-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a89-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86a89-108">Remarks</span></span>  
 <span data-ttu-id="86a89-109">Klasy nie powinny istnieć odwołania po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="86a89-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a89-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86a89-110">Requirements</span></span>  
 <span data-ttu-id="86a89-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a89-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a89-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86a89-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a89-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86a89-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="86a89-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="86a89-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86a89-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86a89-115">See also</span></span>

- [<span data-ttu-id="86a89-116">LoadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="86a89-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="86a89-117">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="86a89-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
