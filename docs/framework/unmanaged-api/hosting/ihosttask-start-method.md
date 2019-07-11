---
title: IHostTask::Start — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bc996973a98f3b8596b449e1524d5c93b4456e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749809"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="764f4-102">IHostTask::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="764f4-102">IHostTask::Start Method</span></span>
<span data-ttu-id="764f4-103">Żądania, że host move — zadanie, reprezentowane przez bieżącą [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia wstrzymane do stanu na żywo, w którym można wykonywać kodu.</span><span class="sxs-lookup"><span data-stu-id="764f4-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="764f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="764f4-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="764f4-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="764f4-105">Return Value</span></span>  
  
|<span data-ttu-id="764f4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="764f4-106">HRESULT</span></span>|<span data-ttu-id="764f4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="764f4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="764f4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="764f4-108">S_OK</span></span>|<span data-ttu-id="764f4-109">Zwrócona pomyślnie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="764f4-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="764f4-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="764f4-110">E_FAIL</span></span>|<span data-ttu-id="764f4-111">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="764f4-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="764f4-112">Gdy metoda zwróci wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="764f4-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="764f4-113">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="764f4-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="764f4-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="764f4-114">Remarks</span></span>  
 <span data-ttu-id="764f4-115">`Start` zawsze zwraca wartość HRESULT S_OK, z wyjątkiem sytuacji, w przypadkach, w którym wystąpił błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="764f4-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="764f4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="764f4-116">Requirements</span></span>  
 <span data-ttu-id="764f4-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="764f4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="764f4-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="764f4-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="764f4-119">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="764f4-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="764f4-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="764f4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764f4-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="764f4-121">See also</span></span>

- [<span data-ttu-id="764f4-122">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="764f4-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="764f4-123">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="764f4-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="764f4-124">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="764f4-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="764f4-125">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="764f4-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
