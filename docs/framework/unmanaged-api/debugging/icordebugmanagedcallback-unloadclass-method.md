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
ms.openlocfilehash: 354de38e106ea16eef10bd9a9cebf2b27ca44d25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548131"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="9bb5c-102">ICorDebugManagedCallback::UnloadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="9bb5c-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="9bb5c-103">Powiadamia debuger jest zwalniany klasy.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bb5c-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bb5c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bb5c-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9bb5c-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji z klasą.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="9bb5c-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bb5c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bb5c-108">Remarks</span></span>  
 <span data-ttu-id="9bb5c-109">Klasy nie powinny istnieć odwołania po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bb5c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bb5c-110">Requirements</span></span>  
 <span data-ttu-id="9bb5c-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bb5c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bb5c-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bb5c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bb5c-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bb5c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bb5c-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bb5c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb5c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bb5c-115">See also</span></span>
- [<span data-ttu-id="9bb5c-116">LoadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="9bb5c-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="9bb5c-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="9bb5c-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
