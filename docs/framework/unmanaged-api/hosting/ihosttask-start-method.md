---
title: "IHostTask::Start — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1a289099245228b8806639cb98f579bc56317b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="67b2b-102">IHostTask::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="67b2b-102">IHostTask::Start Method</span></span>
<span data-ttu-id="67b2b-103">Żądania, że host move — zadanie reprezentowany przez bieżący [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienie z wstrzymane do aktywnego stanu, w którym można wykonywać kodu.</span><span class="sxs-lookup"><span data-stu-id="67b2b-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="67b2b-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="67b2b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="67b2b-105">Return Value</span></span>  
  
|<span data-ttu-id="67b2b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67b2b-106">HRESULT</span></span>|<span data-ttu-id="67b2b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="67b2b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67b2b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="67b2b-108">S_OK</span></span>|<span data-ttu-id="67b2b-109">Zwrócona pomyślnie uruchomić.</span><span class="sxs-lookup"><span data-stu-id="67b2b-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="67b2b-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67b2b-110">E_FAIL</span></span>|<span data-ttu-id="67b2b-111">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="67b2b-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="67b2b-112">Gdy metoda zwróci wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="67b2b-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="67b2b-113">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="67b2b-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67b2b-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67b2b-114">Remarks</span></span>  
 <span data-ttu-id="67b2b-115">`Start`zawsze zwraca wartość HRESULT S_OK, z wyjątkiem przypadków, w którym wystąpił błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="67b2b-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b2b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67b2b-116">Requirements</span></span>  
 <span data-ttu-id="67b2b-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67b2b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67b2b-118">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="67b2b-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67b2b-119">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="67b2b-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67b2b-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67b2b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b2b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67b2b-121">See Also</span></span>  
 [<span data-ttu-id="67b2b-122">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="67b2b-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="67b2b-123">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="67b2b-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="67b2b-124">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="67b2b-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="67b2b-125">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="67b2b-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
