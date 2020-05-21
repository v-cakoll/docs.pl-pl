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
ms.openlocfilehash: 2bf1b8b10aded8e61b9bceab0ee02b1d7c0b752a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762815"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="3d691-102">ICLRTaskManager::GetCurrentTaskType — Metoda</span><span class="sxs-lookup"><span data-stu-id="3d691-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="3d691-103">Pobiera typ zadania, które jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="3d691-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d691-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d691-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d691-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d691-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="3d691-106">określoną Wskaźnik do wartości wyliczenia [ETaskType —](etasktype-enumeration.md) , który wskazuje typ zadania, które jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="3d691-106">[out] A pointer to a value of the [ETaskType](etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d691-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d691-107">Requirements</span></span>  
 <span data-ttu-id="3d691-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d691-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d691-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3d691-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d691-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3d691-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d691-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d691-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d691-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d691-112">See also</span></span>

- [<span data-ttu-id="3d691-113">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="3d691-113">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
