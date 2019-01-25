---
title: EMemoryAvailable — Wyliczenie
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0ffb85dc5f321e45432d6c2fa9448919957f0e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665204"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="c5a4d-102">EMemoryAvailable — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c5a4d-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="c5a4d-103">Zawiera wartości, które wskazują ilość wolnej pamięci fizycznej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c5a4d-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="c5a4d-104">Te wartości logicznie mapowania na zdarzenia dla wysokim i niskim pamięci zwróciło `CreateMemoryResourceNotification` funkcji API Win32.</span><span class="sxs-lookup"><span data-stu-id="c5a4d-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a4d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5a4d-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="c5a4d-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c5a4d-106">Members</span></span>  
  
|<span data-ttu-id="c5a4d-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c5a4d-107">Member</span></span>|<span data-ttu-id="c5a4d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a4d-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="c5a4d-109">Dużej ilości pamięci fizycznej jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="c5a4d-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="c5a4d-110">Bardzo mała ilość pamięci fizycznej jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="c5a4d-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="c5a4d-111">Dostępnej pamięci fizycznej jest neutralna.</span><span class="sxs-lookup"><span data-stu-id="c5a4d-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5a4d-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5a4d-112">Remarks</span></span>  
 <span data-ttu-id="c5a4d-113">Ta wartość jest przekazywana przez hosta do wykonywalnych języka wspólnego (CLR), przy użyciu wywołania do [iclrmemorynotificationcallback::onmemorynotification —](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c5a4d-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a4d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5a4d-114">Requirements</span></span>  
 <span data-ttu-id="c5a4d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5a4d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a4d-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5a4d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5a4d-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5a4d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5a4d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5a4d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a4d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5a4d-119">See also</span></span>
- [<span data-ttu-id="c5a4d-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c5a4d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
