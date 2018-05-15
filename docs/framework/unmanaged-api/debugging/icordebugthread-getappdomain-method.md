---
title: ICorDebugThread::GetAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51878f0334afe52608b60ca540e49c86fded148e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="cb783-102">ICorDebugThread::GetAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb783-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="cb783-103">Pobiera wskaźnika interfejsu do domeny aplikacji, w którym ta ICorDebugThread jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="cb783-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb783-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb783-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb783-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb783-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="cb783-106">[out] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji, w którym ten wątek jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="cb783-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb783-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb783-107">Requirements</span></span>  
 <span data-ttu-id="cb783-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb783-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb783-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb783-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb783-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb783-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb783-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb783-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
