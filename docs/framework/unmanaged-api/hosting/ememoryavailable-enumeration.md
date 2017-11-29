---
title: "EMemoryAvailable — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryAvailable
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryAvailable
helpviewer_keywords: EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c378f2cd9b033e578ff15472a10a6dc295ad6539
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="7d399-102">EMemoryAvailable — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7d399-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="7d399-103">Zawiera wartości, które wskazują ilość wolnej pamięci fizycznej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7d399-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="7d399-104">Te wartości logicznie mapowania na zdarzenia dla wysoki i niski pamięci zwrócony z `CreateMemoryResourceNotification` funkcji w interfejsie API Win32.</span><span class="sxs-lookup"><span data-stu-id="7d399-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d399-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d399-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="7d399-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7d399-106">Members</span></span>  
  
|<span data-ttu-id="7d399-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7d399-107">Member</span></span>|<span data-ttu-id="7d399-108">Opis</span><span class="sxs-lookup"><span data-stu-id="7d399-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="7d399-109">Dużej ilości pamięci fizycznej dostępnej.</span><span class="sxs-lookup"><span data-stu-id="7d399-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="7d399-110">Dostępna jest bardzo mała ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="7d399-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="7d399-111">Neutralne jest dostępnej pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="7d399-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d399-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d399-112">Remarks</span></span>  
 <span data-ttu-id="7d399-113">Ta wartość jest przekazywana przez środowisko uruchomieniowe języka wspólnego (CLR) przez hosta przy użyciu wywołania do [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7d399-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d399-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d399-114">Requirements</span></span>  
 <span data-ttu-id="7d399-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d399-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d399-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d399-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d399-117">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d399-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d399-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d399-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d399-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d399-119">See Also</span></span>  
 [<span data-ttu-id="7d399-120">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7d399-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
