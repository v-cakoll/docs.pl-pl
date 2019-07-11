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
ms.openlocfilehash: 629a4850d47940633c8c69a7e464cfae315b3c56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761244"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="bf306-102">ICorDebugManagedCallback::UnloadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf306-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="bf306-103">Powiadamia debuger jest zwalniany klasy.</span><span class="sxs-lookup"><span data-stu-id="bf306-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf306-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf306-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf306-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf306-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bf306-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji z klasą.</span><span class="sxs-lookup"><span data-stu-id="bf306-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="bf306-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="bf306-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf306-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf306-108">Remarks</span></span>  
 <span data-ttu-id="bf306-109">Klasy nie powinny istnieć odwołania po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="bf306-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf306-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf306-110">Requirements</span></span>  
 <span data-ttu-id="bf306-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf306-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf306-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf306-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf306-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf306-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf306-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf306-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf306-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf306-115">See also</span></span>

- [<span data-ttu-id="bf306-116">LoadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="bf306-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="bf306-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf306-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
