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
ms.openlocfilehash: d98a0c1c3187b81c44fae6eee91d975169a40045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072809"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="1094a-102">EMemoryAvailable — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1094a-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="1094a-103">Zawiera wartości, które wskazują ilość wolnej pamięci fizycznej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1094a-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="1094a-104">Te wartości logicznie mapowania na zdarzenia dla wysokim i niskim pamięci zwróciło `CreateMemoryResourceNotification` funkcji w interfejsie API Windows.</span><span class="sxs-lookup"><span data-stu-id="1094a-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1094a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1094a-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="1094a-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1094a-106">Members</span></span>  
  
|<span data-ttu-id="1094a-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1094a-107">Member</span></span>|<span data-ttu-id="1094a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="1094a-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="1094a-109">Dużej ilości pamięci fizycznej jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="1094a-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="1094a-110">Bardzo mała ilość pamięci fizycznej jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="1094a-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="1094a-111">Dostępnej pamięci fizycznej jest neutralna.</span><span class="sxs-lookup"><span data-stu-id="1094a-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1094a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1094a-112">Remarks</span></span>  
 <span data-ttu-id="1094a-113">Ta wartość jest przekazywana przez hosta do wykonywalnych języka wspólnego (CLR), przy użyciu wywołania do [iclrmemorynotificationcallback::onmemorynotification —](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1094a-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1094a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1094a-114">Requirements</span></span>  
 <span data-ttu-id="1094a-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1094a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1094a-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1094a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1094a-117">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1094a-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1094a-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1094a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1094a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1094a-119">See also</span></span>

- [<span data-ttu-id="1094a-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1094a-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
