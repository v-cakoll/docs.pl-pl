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
ms.openlocfilehash: d76242eb8539f2e8dffbf39b7eaf595664bdce8e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842026"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="3df02-102">IHostTaskManager::GetStackGuarantee — Metoda</span><span class="sxs-lookup"><span data-stu-id="3df02-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="3df02-103">Pobiera ilość miejsca na stosie, która ma być dostępna po zakończeniu operacji stosu, ale przed zamknięciem procesu.</span><span class="sxs-lookup"><span data-stu-id="3df02-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3df02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3df02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3df02-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="3df02-106">określoną Wskaźnik do liczby dostępnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="3df02-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3df02-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3df02-107">Requirements</span></span>  
 <span data-ttu-id="3df02-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df02-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df02-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3df02-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3df02-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3df02-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3df02-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3df02-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df02-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3df02-112">See also</span></span>

- [<span data-ttu-id="3df02-113">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3df02-113">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
