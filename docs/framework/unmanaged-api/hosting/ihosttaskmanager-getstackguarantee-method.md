---
title: IHostTaskManager::GetStackGuarantee — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea1c1f998febccbc80fb10cef5a8dfd229e1987e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095949"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="b1d03-102">IHostTaskManager::GetStackGuarantee — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1d03-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="b1d03-103">Pobiera ilość miejsca stosu, który może być dostępna po zakończeniu operacji stosu, ale przed zamknięciem procesu.</span><span class="sxs-lookup"><span data-stu-id="b1d03-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1d03-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1d03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1d03-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="b1d03-106">[out] Wskaźnik do liczby bajtów, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="b1d03-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d03-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1d03-107">Requirements</span></span>  
 <span data-ttu-id="b1d03-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1d03-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d03-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1d03-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1d03-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1d03-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b1d03-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b1d03-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1d03-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1d03-112">See also</span></span>

- [<span data-ttu-id="b1d03-113">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1d03-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
