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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789405"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="a332a-102">IHostTaskManager::GetStackGuarantee — Metoda</span><span class="sxs-lookup"><span data-stu-id="a332a-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="a332a-103">Pobiera ilość miejsca stosu, który może być dostępna po zakończeniu operacji stosu, ale przed zamknięciem procesu.</span><span class="sxs-lookup"><span data-stu-id="a332a-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a332a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a332a-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a332a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a332a-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="a332a-106">[out] Wskaźnik do liczby bajtów, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="a332a-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a332a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a332a-107">Requirements</span></span>  
 <span data-ttu-id="a332a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a332a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a332a-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a332a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a332a-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a332a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a332a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a332a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a332a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a332a-112">See also</span></span>

- [<span data-ttu-id="a332a-113">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a332a-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
