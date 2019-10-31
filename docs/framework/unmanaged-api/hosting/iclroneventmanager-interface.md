---
title: ICLROnEventManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140843"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="b6483-102">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b6483-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="b6483-103">Zapewnia metody, które pozwalają hostowi rejestrować i wyrejestrować wywołania zwrotne dla zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="b6483-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6483-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b6483-104">Methods</span></span>  
  
|<span data-ttu-id="b6483-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b6483-105">Method</span></span>|<span data-ttu-id="b6483-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b6483-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6483-107">RegisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="b6483-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="b6483-108">Rejestruje wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b6483-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="b6483-109">UnregisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="b6483-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="b6483-110">Wyrejestrowuje wcześniej zarejestrowany wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b6483-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6483-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6483-111">Remarks</span></span>  
 <span data-ttu-id="b6483-112">Aby zarejestrować i wyrejestrować wywołania zwrotne zdarzeń, Host pobiera odwołanie do `ICLROnEventManager` przez wywołanie metody [ICLRControl:: GetCLRManager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6483-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6483-113">Zdarzenia opisane przez [EClrEvent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="b6483-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6483-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6483-114">Requirements</span></span>  
 <span data-ttu-id="b6483-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6483-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6483-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6483-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6483-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6483-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6483-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6483-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6483-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6483-119">See also</span></span>

- [<span data-ttu-id="b6483-120">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b6483-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="b6483-121">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6483-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="b6483-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6483-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b6483-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6483-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
