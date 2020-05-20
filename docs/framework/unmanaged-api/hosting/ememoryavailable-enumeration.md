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
ms.openlocfilehash: 822396e28d000a5309738680fec502e1aeacd67c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616219"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="021b2-102">EMemoryAvailable — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="021b2-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="021b2-103">Zawiera wartości wskazujące ilość wolnej pamięci fizycznej na komputerze.</span><span class="sxs-lookup"><span data-stu-id="021b2-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="021b2-104">Te wartości logicznie mapują do zdarzeń związanych z wysoką i niską ilością pamięci zwracaną z `CreateMemoryResourceNotification` funkcji w interfejsie API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="021b2-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="021b2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="021b2-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="021b2-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="021b2-106">Members</span></span>  
  
|<span data-ttu-id="021b2-107">Członek</span><span class="sxs-lookup"><span data-stu-id="021b2-107">Member</span></span>|<span data-ttu-id="021b2-108">Opis</span><span class="sxs-lookup"><span data-stu-id="021b2-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="021b2-109">Dostępna jest duża ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="021b2-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="021b2-110">Dostępna jest bardzo mała ilość pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="021b2-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="021b2-111">Dostępna pamięć fizyczna jest neutralna.</span><span class="sxs-lookup"><span data-stu-id="021b2-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="021b2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="021b2-112">Remarks</span></span>  
 <span data-ttu-id="021b2-113">Ta wartość jest przesyłana przez hosta do środowiska uruchomieniowego języka wspólnego (CLR) za pomocą wywołania metody [ICLRMemoryNotificationCallback:: OnMemoryNotification —](iclrmemorynotificationcallback-onmemorynotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="021b2-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="021b2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="021b2-114">Requirements</span></span>  
 <span data-ttu-id="021b2-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="021b2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="021b2-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="021b2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="021b2-117">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="021b2-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="021b2-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="021b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="021b2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="021b2-119">See also</span></span>

- [<span data-ttu-id="021b2-120">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="021b2-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
