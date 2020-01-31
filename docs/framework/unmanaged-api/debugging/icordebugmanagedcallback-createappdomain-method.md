---
title: ICorDebugManagedCallback::CreateAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 35ea69d32ee9b994cc0bf91339c798edcd472f44
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788429"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="a48bc-102">ICorDebugManagedCallback::CreateAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="a48bc-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="a48bc-103">Powiadamia debuger o utworzeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a48bc-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a48bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a48bc-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a48bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a48bc-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a48bc-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, w którym została utworzona domena aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a48bc-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a48bc-107">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która została utworzona.</span><span class="sxs-lookup"><span data-stu-id="a48bc-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a48bc-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a48bc-108">Requirements</span></span>  
 <span data-ttu-id="a48bc-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a48bc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a48bc-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a48bc-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a48bc-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a48bc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a48bc-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a48bc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48bc-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a48bc-113">See also</span></span>

- [<span data-ttu-id="a48bc-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a48bc-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
