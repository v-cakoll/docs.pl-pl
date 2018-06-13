---
title: ICLRSyncManager::DeleteRWLockOwnerIterator — Metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ee4a09902be093bdbfe0b367f4add35bdda571c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434070"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="b6bc9-102">ICLRSyncManager::DeleteRWLockOwnerIterator — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6bc9-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="b6bc9-103">Żąda, że środowisko uruchomieniowe języka wspólnego (CLR) zniszczyć iterację, która została utworzona przez wywołanie do [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span><span class="sxs-lookup"><span data-stu-id="b6bc9-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6bc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6bc9-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6bc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6bc9-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="b6bc9-106">[in] Iterator, który został utworzony za pomocą wywołania `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6bc9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b6bc9-107">Return Value</span></span>  
  
|<span data-ttu-id="b6bc9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6bc9-108">HRESULT</span></span>|<span data-ttu-id="b6bc9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b6bc9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6bc9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6bc9-110">S_OK</span></span>|<span data-ttu-id="b6bc9-111">`DeleteRWLockOwnerIterator` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="b6bc9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6bc9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6bc9-113">Środowisko CLR nie został załadowany do procesu lub jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="b6bc9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b6bc9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b6bc9-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-115">The call timed out.</span></span>|  
|<span data-ttu-id="b6bc9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b6bc9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b6bc9-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b6bc9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b6bc9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b6bc9-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b6bc9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b6bc9-120">E_FAIL</span></span>|<span data-ttu-id="b6bc9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b6bc9-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b6bc9-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6bc9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6bc9-124">Remarks</span></span>  
 <span data-ttu-id="b6bc9-125">Tę metodę można wywołać hosta i `CreateRWLockOwnerIterator` aby upewnić się, że jej implementacja wątków pozostaje zsynchronizowany.</span><span class="sxs-lookup"><span data-stu-id="b6bc9-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6bc9-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6bc9-126">Requirements</span></span>  
 <span data-ttu-id="b6bc9-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6bc9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6bc9-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6bc9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6bc9-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6bc9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6bc9-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6bc9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bc9-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6bc9-131">See Also</span></span>  
 [<span data-ttu-id="b6bc9-132">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6bc9-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="b6bc9-133">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6bc9-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
