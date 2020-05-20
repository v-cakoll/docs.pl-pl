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
ms.openlocfilehash: 30312e6e09535cee2968b1f9e8ac87b461c5ff40
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703520"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="7d4ca-102">ICLROnEventManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7d4ca-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="7d4ca-103">Zapewnia metody, które pozwalają hostowi rejestrować i wyrejestrować wywołania zwrotne dla zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="7d4ca-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d4ca-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7d4ca-104">Methods</span></span>  
  
|<span data-ttu-id="7d4ca-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7d4ca-105">Method</span></span>|<span data-ttu-id="7d4ca-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7d4ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d4ca-107">RegisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="7d4ca-107">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="7d4ca-108">Rejestruje wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7d4ca-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="7d4ca-109">UnregisterActionOnEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="7d4ca-109">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="7d4ca-110">Wyrejestrowuje wcześniej zarejestrowany wskaźnik wywołania zwrotnego dla określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7d4ca-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d4ca-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d4ca-111">Remarks</span></span>  
 <span data-ttu-id="7d4ca-112">Aby zarejestrować i wyrejestrować wywołania zwrotne zdarzeń, Host pobiera odwołanie do, `ICLROnEventManager` wywołując metodę [ICLRControl:: GetCLRManager —](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7d4ca-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d4ca-113">Zdarzenia opisane przez [EClrEvent —](eclrevent-enumeration.md) mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="7d4ca-113">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d4ca-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d4ca-114">Requirements</span></span>  
 <span data-ttu-id="7d4ca-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d4ca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d4ca-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7d4ca-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d4ca-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7d4ca-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d4ca-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d4ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d4ca-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d4ca-119">See also</span></span>

- [<span data-ttu-id="7d4ca-120">EClrEvent, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7d4ca-120">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="7d4ca-121">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7d4ca-121">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="7d4ca-122">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7d4ca-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7d4ca-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7d4ca-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
