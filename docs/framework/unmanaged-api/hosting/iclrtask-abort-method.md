---
title: ICLRTask::Abort — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46d60ff6ab64d57ca5c7020877758657b61125ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434840"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="16eab-102">ICLRTask::Abort — Metoda</span><span class="sxs-lookup"><span data-stu-id="16eab-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="16eab-103">Żądania, że środowisko uruchomieniowe języka wspólnego (CLR) przerwać zadanie który bieżącego [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) reprezentuje wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="16eab-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16eab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16eab-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="16eab-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="16eab-105">Return Value</span></span>  
  
|<span data-ttu-id="16eab-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16eab-106">HRESULT</span></span>|<span data-ttu-id="16eab-107">Opis</span><span class="sxs-lookup"><span data-stu-id="16eab-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16eab-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="16eab-108">S_OK</span></span>|<span data-ttu-id="16eab-109">`Abort` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="16eab-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="16eab-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="16eab-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="16eab-111">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="16eab-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="16eab-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="16eab-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="16eab-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="16eab-113">The call timed out.</span></span>|  
|<span data-ttu-id="16eab-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="16eab-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="16eab-115">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="16eab-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="16eab-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="16eab-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="16eab-117">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="16eab-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="16eab-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="16eab-118">E_FAIL</span></span>|<span data-ttu-id="16eab-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="16eab-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="16eab-120">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="16eab-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="16eab-121">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="16eab-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16eab-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16eab-122">Remarks</span></span>  
 <span data-ttu-id="16eab-123">Uruchamia środowisko CLR <xref:System.Threading.ThreadAbortException> podczas wywołania hosta `Abort`.</span><span class="sxs-lookup"><span data-stu-id="16eab-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="16eab-124">Zwraca natychmiast po informacje o wyjątku został zainicjowany, bez oczekiwania na kod użytkownika, takie jak finalizatory lub mechanizmy obsługi wyjątków do wykonania.</span><span class="sxs-lookup"><span data-stu-id="16eab-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="16eab-125">Wywołuje się `Abort` w związku z tym szybkiego powrotu.</span><span class="sxs-lookup"><span data-stu-id="16eab-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16eab-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16eab-126">Requirements</span></span>  
 <span data-ttu-id="16eab-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16eab-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16eab-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="16eab-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16eab-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16eab-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16eab-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16eab-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16eab-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16eab-131">See Also</span></span>  
 [<span data-ttu-id="16eab-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="16eab-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="16eab-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="16eab-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="16eab-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="16eab-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="16eab-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="16eab-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
