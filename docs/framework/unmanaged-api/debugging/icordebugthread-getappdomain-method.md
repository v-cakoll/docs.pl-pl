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
ms.openlocfilehash: 12a37ee8367006975b0f8ee4fa638ae3d72f9486
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987132"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="5c92c-102">ICorDebugThread::GetAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c92c-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="5c92c-103">Pobiera wskaźnik interfejsu do domeny aplikacji, w którym ta ICorDebugThread jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c92c-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c92c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c92c-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c92c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c92c-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="5c92c-106">[out] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w którym ten wątek jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c92c-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c92c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c92c-107">Requirements</span></span>  
 <span data-ttu-id="5c92c-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c92c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c92c-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c92c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c92c-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c92c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c92c-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c92c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
