---
title: ICorDebugManagedCallback::LoadModule — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfca06c656f3274f4c5ddb06373a0296dc5e6905
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164544"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="97d28-102">ICorDebugManagedCallback::LoadModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="97d28-102">ICorDebugManagedCallback::LoadModule Method</span></span>
<span data-ttu-id="97d28-103">Powiadamia debuger pomyślnie załadowano moduł środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="97d28-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97d28-104">Syntax</span></span>  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97d28-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="97d28-106">[in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, do którego moduł został załadowany.</span><span class="sxs-lookup"><span data-stu-id="97d28-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="97d28-107">[in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł CLR.</span><span class="sxs-lookup"><span data-stu-id="97d28-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d28-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97d28-108">Remarks</span></span>  
 <span data-ttu-id="97d28-109">`LoadModule` Wywołanie zwrotne odpowiedni moment, aby zbadać metadane dla modułu, Ustaw flagi kompilatora just-in-time (JIT) lub włączyć lub wyłączyć klasy ładującej wywołania zwrotne modułu.</span><span class="sxs-lookup"><span data-stu-id="97d28-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d28-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97d28-110">Requirements</span></span>  
 <span data-ttu-id="97d28-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97d28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d28-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97d28-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97d28-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97d28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97d28-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d28-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97d28-115">See also</span></span>

- [<span data-ttu-id="97d28-116">UnloadModule, metoda</span><span class="sxs-lookup"><span data-stu-id="97d28-116">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="97d28-117">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="97d28-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
