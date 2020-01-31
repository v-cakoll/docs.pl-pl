---
title: ICorDebugManagedCallback::ExitAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: 7bfa71ccff4a65e72a6b548a09d27648b67c0ae5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781855"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="2d3c4-102">ICorDebugManagedCallback::ExitAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="2d3c4-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="2d3c4-103">Powiadamia debuger o zakończeniu domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d3c4-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d3c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d3c4-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d3c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d3c4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="2d3c4-106">podczas Wskaźnik do obiektu ICorDebugProcess, który reprezentuje proces, który zawiera daną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2d3c4-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="2d3c4-107">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która została zakończona.</span><span class="sxs-lookup"><span data-stu-id="2d3c4-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d3c4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d3c4-108">Requirements</span></span>  
 <span data-ttu-id="2d3c4-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d3c4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d3c4-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d3c4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d3c4-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2d3c4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d3c4-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d3c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3c4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d3c4-113">See also</span></span>

- [<span data-ttu-id="2d3c4-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d3c4-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
