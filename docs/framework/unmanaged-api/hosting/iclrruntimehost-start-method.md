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
ms.openlocfilehash: a599e754202309a2b61d1761150f3f570fd0dc76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120411"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="6ca25-102">ICLRRuntimeHost::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ca25-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="6ca25-103">Inicjuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu.</span><span class="sxs-lookup"><span data-stu-id="6ca25-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ca25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ca25-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6ca25-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ca25-105">Return Value</span></span>  
  
|<span data-ttu-id="6ca25-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ca25-106">HRESULT</span></span>|<span data-ttu-id="6ca25-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6ca25-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ca25-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ca25-108">S_OK</span></span>|<span data-ttu-id="6ca25-109">`Start` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="6ca25-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="6ca25-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ca25-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ca25-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6ca25-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ca25-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ca25-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ca25-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6ca25-113">The call timed out.</span></span>|  
|<span data-ttu-id="6ca25-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ca25-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ca25-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6ca25-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ca25-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ca25-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ca25-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="6ca25-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ca25-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ca25-118">E_FAIL</span></span>|<span data-ttu-id="6ca25-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6ca25-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ca25-120">Jeśli metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="6ca25-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ca25-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6ca25-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ca25-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ca25-122">Remarks</span></span>  
 <span data-ttu-id="6ca25-123">W wielu scenariuszach nie jest konieczne wywoływanie `Start`, ponieważ środowisko uruchomieniowe zostanie automatycznie zainicjowane podczas pierwszego żądania uruchomienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6ca25-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="6ca25-124">Można jednak użyć `Start`, aby określić dokładnie czas inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6ca25-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ca25-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ca25-125">Requirements</span></span>  
 <span data-ttu-id="6ca25-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ca25-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ca25-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ca25-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ca25-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ca25-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ca25-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ca25-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ca25-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ca25-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="6ca25-131">ICLRRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ca25-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
