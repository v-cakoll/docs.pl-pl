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
ms.openlocfilehash: 739670fb84eb0145fd8bf8073f453518487c38b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749571"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="0604b-102">IHostTaskManager::GetStackGuarantee — Metoda</span><span class="sxs-lookup"><span data-stu-id="0604b-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="0604b-103">Pobiera ilość miejsca stosu, który może być dostępna po zakończeniu operacji stosu, ale przed zamknięciem procesu.</span><span class="sxs-lookup"><span data-stu-id="0604b-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0604b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0604b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0604b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0604b-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="0604b-106">[out] Wskaźnik do liczby bajtów, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="0604b-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0604b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0604b-107">Requirements</span></span>  
 <span data-ttu-id="0604b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0604b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0604b-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0604b-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0604b-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0604b-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0604b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0604b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0604b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0604b-112">See also</span></span>

- [<span data-ttu-id="0604b-113">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0604b-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
