---
title: "IHostTaskManager::GetStackGuarantee — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.GetStackGuarantee
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 691eaa2bd462af5fff0b222e991c13032ddb1af1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="229e1-102">IHostTaskManager::GetStackGuarantee — Metoda</span><span class="sxs-lookup"><span data-stu-id="229e1-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="229e1-103">Pobiera ilość miejsca na stosie, który może być dostępne po zakończeniu operacji stosu, ale przed zamknięciem procesu.</span><span class="sxs-lookup"><span data-stu-id="229e1-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="229e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="229e1-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="229e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="229e1-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="229e1-106">[out] Wskaźnik do liczba bajtów, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="229e1-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="229e1-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="229e1-107">Requirements</span></span>  
 <span data-ttu-id="229e1-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="229e1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="229e1-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="229e1-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="229e1-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="229e1-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="229e1-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="229e1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="229e1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="229e1-112">See Also</span></span>  
 [<span data-ttu-id="229e1-113">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="229e1-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
