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
ms.openlocfilehash: 22ec34c82d0f8e550dfc8941f2c048ebed6cf1d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133038"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="73986-102">IHostTaskManager::GetStackGuarantee — Metoda</span><span class="sxs-lookup"><span data-stu-id="73986-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="73986-103">Pobiera ilość miejsca na stosie, która ma być dostępna po zakończeniu operacji stosu, ale przed zamknięciem procesu.</span><span class="sxs-lookup"><span data-stu-id="73986-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73986-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73986-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73986-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73986-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="73986-106">określoną Wskaźnik do liczby dostępnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="73986-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73986-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73986-107">Requirements</span></span>  
 <span data-ttu-id="73986-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73986-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73986-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="73986-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73986-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="73986-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73986-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73986-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73986-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73986-112">See also</span></span>

- [<span data-ttu-id="73986-113">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="73986-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
