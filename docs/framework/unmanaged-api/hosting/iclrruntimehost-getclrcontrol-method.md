---
title: ICLRRuntimeHost::GetCLRControl — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86858d5fe5bf9ac07a91e810599c27a479141f4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435058"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="3e66a-102">ICLRRuntimeHost::GetCLRControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="3e66a-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="3e66a-103">Pobiera wskaźnika interfejsu typu [ICLRControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) hostów może być dostosowanie właściwości środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="3e66a-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e66a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e66a-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e66a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e66a-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="3e66a-106">[out] Wskaźnik interfejsu typu [ICLRControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , który umożliwia hostów skonfigurować dodatkowe aspekty środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="3e66a-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e66a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3e66a-107">Return Value</span></span>  
  
|<span data-ttu-id="3e66a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e66a-108">HRESULT</span></span>|<span data-ttu-id="3e66a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3e66a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e66a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e66a-110">S_OK</span></span>|<span data-ttu-id="3e66a-111">`GetCLRControl` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3e66a-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="3e66a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e66a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e66a-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="3e66a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e66a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e66a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e66a-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="3e66a-115">The call timed out.</span></span>|  
|<span data-ttu-id="3e66a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e66a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e66a-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="3e66a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e66a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e66a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e66a-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="3e66a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e66a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e66a-120">E_FAIL</span></span>|<span data-ttu-id="3e66a-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3e66a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e66a-122">Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="3e66a-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e66a-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3e66a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e66a-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3e66a-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3e66a-125">Środowisko CLR został już uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="3e66a-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e66a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e66a-126">Remarks</span></span>  
 <span data-ttu-id="3e66a-127">`ICLRControl` udostępnia [GetCLRManager — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodę, która umożliwia hosta otrzymywać wskaźnik interfejsu do jednego z typów menedżera.</span><span class="sxs-lookup"><span data-stu-id="3e66a-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e66a-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e66a-128">Requirements</span></span>  
 <span data-ttu-id="3e66a-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e66a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e66a-130">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e66a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e66a-131">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e66a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e66a-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e66a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e66a-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e66a-133">See Also</span></span>  
 [<span data-ttu-id="3e66a-134">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e66a-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="3e66a-135">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e66a-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
