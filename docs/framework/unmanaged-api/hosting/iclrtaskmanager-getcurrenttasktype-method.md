---
title: ICLRTaskManager::GetCurrentTaskType — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51c103fb38dd97ec076096037932925e31280f02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437719"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="1a179-102">ICLRTaskManager::GetCurrentTaskType — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a179-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="1a179-103">Pobiera typ zadania, które jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="1a179-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a179-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a179-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a179-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a179-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="1a179-106">[out] Wskaźnik do wartości [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) wyliczenia wskazująca typ zadania, które jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="1a179-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a179-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a179-107">Requirements</span></span>  
 <span data-ttu-id="1a179-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a179-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a179-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1a179-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a179-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a179-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a179-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a179-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a179-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a179-112">See Also</span></span>  
 [<span data-ttu-id="1a179-113">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a179-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
