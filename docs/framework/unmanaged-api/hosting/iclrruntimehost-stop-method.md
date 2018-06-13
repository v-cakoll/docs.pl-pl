---
title: ICLRRuntimeHost::Stop — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d479e271c2cc4ebf9ea6ff349fd28bff37c3857
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436101"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="deccb-102">ICLRRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="deccb-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="deccb-103">Zatrzymuje wykonywanie kodu przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="deccb-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="deccb-104">Ta metoda nie zwolnić zasoby do hosta, wyładować domeny aplikacji lub zniszczenie wątków.</span><span class="sxs-lookup"><span data-stu-id="deccb-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="deccb-105">Należy zakończyć ten proces, aby zwolnić zasoby.</span><span class="sxs-lookup"><span data-stu-id="deccb-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deccb-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="deccb-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="deccb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="deccb-107">Return Value</span></span>  
  
|<span data-ttu-id="deccb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="deccb-108">HRESULT</span></span>|<span data-ttu-id="deccb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="deccb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="deccb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="deccb-110">S_OK</span></span>|<span data-ttu-id="deccb-111">`Stop` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="deccb-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="deccb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="deccb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="deccb-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="deccb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="deccb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="deccb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="deccb-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="deccb-115">The call timed out.</span></span>|  
|<span data-ttu-id="deccb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="deccb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="deccb-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="deccb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="deccb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="deccb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="deccb-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="deccb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="deccb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="deccb-120">E_FAIL</span></span>|<span data-ttu-id="deccb-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="deccb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="deccb-122">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="deccb-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="deccb-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="deccb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="deccb-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="deccb-124">Requirements</span></span>  
 <span data-ttu-id="deccb-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deccb-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deccb-126">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="deccb-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="deccb-127">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="deccb-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="deccb-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deccb-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deccb-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="deccb-129">See Also</span></span>  
 [<span data-ttu-id="deccb-130">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="deccb-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
