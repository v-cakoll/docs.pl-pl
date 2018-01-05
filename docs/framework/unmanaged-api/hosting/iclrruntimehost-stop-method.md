---
title: "ICLRRuntimeHost::Stop — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cb9eaecdec661ae56727e5fd38c7e9a3b9621d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="f8abc-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8abc-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="f8abc-103">Zatrzymuje wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f8abc-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f8abc-104">Ta metoda nie zwolnić zasoby do hosta, wyładować domeny aplikacji lub zniszczenie wątków.</span><span class="sxs-lookup"><span data-stu-id="f8abc-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="f8abc-105">Należy zakończyć ten proces, aby zwolnić zasoby.</span><span class="sxs-lookup"><span data-stu-id="f8abc-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8abc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8abc-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f8abc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f8abc-107">Return Value</span></span>  
  
|<span data-ttu-id="f8abc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8abc-108">HRESULT</span></span>|<span data-ttu-id="f8abc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f8abc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8abc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8abc-110">S_OK</span></span>|<span data-ttu-id="f8abc-111">`Stop`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f8abc-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="f8abc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8abc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8abc-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f8abc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8abc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8abc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8abc-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f8abc-115">The call timed out.</span></span>|  
|<span data-ttu-id="f8abc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8abc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8abc-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f8abc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8abc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8abc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8abc-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f8abc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8abc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8abc-120">E_FAIL</span></span>|<span data-ttu-id="f8abc-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f8abc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8abc-122">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f8abc-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8abc-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f8abc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8abc-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8abc-124">Requirements</span></span>  
 <span data-ttu-id="f8abc-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8abc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8abc-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8abc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8abc-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8abc-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8abc-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8abc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8abc-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8abc-129">See Also</span></span>  
 [<span data-ttu-id="f8abc-130">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8abc-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
