---
title: ICLRRuntimeHost::Start — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608612f6a0f4395092e33ce75fdbd249f19ae4f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172617"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="a84c0-102">ICLRRuntimeHost::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="a84c0-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="a84c0-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="a84c0-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a84c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a84c0-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a84c0-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a84c0-105">Return Value</span></span>  
  
|<span data-ttu-id="a84c0-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a84c0-106">HRESULT</span></span>|<span data-ttu-id="a84c0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a84c0-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a84c0-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a84c0-108">S_OK</span></span>|<span data-ttu-id="a84c0-109">`Start` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a84c0-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="a84c0-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a84c0-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a84c0-111">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a84c0-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a84c0-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a84c0-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a84c0-113">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a84c0-113">The call timed out.</span></span>|  
|<span data-ttu-id="a84c0-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a84c0-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a84c0-115">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a84c0-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a84c0-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a84c0-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a84c0-117">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a84c0-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a84c0-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a84c0-118">E_FAIL</span></span>|<span data-ttu-id="a84c0-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a84c0-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a84c0-120">Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a84c0-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a84c0-121">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a84c0-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a84c0-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a84c0-122">Remarks</span></span>  
 <span data-ttu-id="a84c0-123">W wielu scenariuszach nie jest konieczne do wywołania `Start`, ponieważ środowisko uruchomieniowe będzie inicjował się automatycznie na pierwsze żądanie do uruchomienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a84c0-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="a84c0-124">Można jednak użyć `Start` określić dokładnie w gdy środowisko wykonawcze powinno zostać zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="a84c0-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a84c0-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a84c0-125">Requirements</span></span>  
 <span data-ttu-id="a84c0-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a84c0-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a84c0-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a84c0-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a84c0-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a84c0-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a84c0-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a84c0-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84c0-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a84c0-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="a84c0-131">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a84c0-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
