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
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176438"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="b6020-102">EMemoryAvailable — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b6020-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="b6020-103">Zawiera wartości wskazujące ilość wolnej pamięci fizycznej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b6020-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="b6020-104">Wartości te logicznie mapują zdarzenia dla wysokiej `CreateMemoryResourceNotification` i małej ilości pamięci zwróconej z funkcji w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b6020-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6020-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6020-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="b6020-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b6020-106">Members</span></span>  
  
|<span data-ttu-id="b6020-107">Członek</span><span class="sxs-lookup"><span data-stu-id="b6020-107">Member</span></span>|<span data-ttu-id="b6020-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b6020-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="b6020-109">Dostępnych jest mnóstwo pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="b6020-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="b6020-110">Dostępna jest bardzo mała pamięć fizyczna.</span><span class="sxs-lookup"><span data-stu-id="b6020-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="b6020-111">Dostępna pamięć fizyczna jest neutralna.</span><span class="sxs-lookup"><span data-stu-id="b6020-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6020-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6020-112">Remarks</span></span>  
 <span data-ttu-id="b6020-113">Ta wartość jest przekazywana przez hosta do środowiska wykonawczego języka wspólnego (CLR) przy użyciu wywołania [metody ICLRMemoryNotificationCallback::OnMemoryNotification.](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)</span><span class="sxs-lookup"><span data-stu-id="b6020-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6020-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6020-114">Requirements</span></span>  
 <span data-ttu-id="b6020-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6020-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6020-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b6020-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6020-117">**Biblioteka:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b6020-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6020-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6020-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6020-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6020-119">See also</span></span>

- [<span data-ttu-id="b6020-120">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b6020-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
