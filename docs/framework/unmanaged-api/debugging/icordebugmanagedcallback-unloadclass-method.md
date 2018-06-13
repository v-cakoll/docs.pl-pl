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
ms.openlocfilehash: e70a1c66baff2d91554dea47e248a7003e30c498
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414615"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="eb287-102">ICorDebugManagedCallback::UnloadClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb287-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="eb287-103">Powiadamia debugera jest zwalniany klasy.</span><span class="sxs-lookup"><span data-stu-id="eb287-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb287-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb287-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb287-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb287-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="eb287-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje z klasą domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb287-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="eb287-107">[in] Wskaźnik do obiektu ICorDebugClass, który reprezentuje klasę.</span><span class="sxs-lookup"><span data-stu-id="eb287-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb287-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb287-108">Remarks</span></span>  
 <span data-ttu-id="eb287-109">Klasa nie ma być utworzone odwołanie po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="eb287-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb287-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb287-110">Requirements</span></span>  
 <span data-ttu-id="eb287-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb287-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb287-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb287-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb287-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb287-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb287-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb287-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb287-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb287-115">See Also</span></span>  
 [<span data-ttu-id="eb287-116">LoadClass, metoda</span><span class="sxs-lookup"><span data-stu-id="eb287-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)  
 [<span data-ttu-id="eb287-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb287-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
