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
ms.openlocfilehash: da473ed176ab6c69ed974d5f28b22fc8eb30c6af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762521"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="e63c3-102">ICorDebugThread::GetAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="e63c3-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="e63c3-103">Pobiera wskaźnik interfejsu do domeny aplikacji, w którym ta ICorDebugThread jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e63c3-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e63c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e63c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e63c3-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="e63c3-106">[out] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w którym ten wątek jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e63c3-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e63c3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e63c3-107">Requirements</span></span>  
 <span data-ttu-id="e63c3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e63c3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e63c3-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e63c3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e63c3-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e63c3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e63c3-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e63c3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
