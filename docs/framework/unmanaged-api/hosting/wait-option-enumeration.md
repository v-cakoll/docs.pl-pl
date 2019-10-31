---
title: WAIT_OPTION — Wyliczenie
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 9ecfb551b55551e5f6cc7e7e9ffb55e5a96259ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141515"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="6592d-102">WAIT_OPTION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6592d-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="6592d-103">Zawiera wartości wskazujące akcję, którą host powinien wykonać, jeśli operacja zażądała bloków środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="6592d-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6592d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6592d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="6592d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6592d-105">Members</span></span>  
  
|<span data-ttu-id="6592d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6592d-106">Member</span></span>|<span data-ttu-id="6592d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6592d-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="6592d-108">Powiadamia hosta, że zadanie powinno zostać wznowione, jeśli środowisko CLR wywoła metodę [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6592d-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="6592d-109">Powiadamia hosta, że musi pompować komunikaty w bieżącym wątku systemu operacyjnego, jeśli wątek zostanie zablokowany.</span><span class="sxs-lookup"><span data-stu-id="6592d-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="6592d-110">Środowisko uruchomieniowe określa tę wartość tylko w wątku <xref:System.Threading.ApartmentState.STA>.</span><span class="sxs-lookup"><span data-stu-id="6592d-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="6592d-111">Powiadamia hosta, że nie można rozbić określonego żądania synchronizacji przez hosta.</span><span class="sxs-lookup"><span data-stu-id="6592d-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="6592d-112">Oznacza to, że host nie może zwrócić `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="6592d-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6592d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6592d-113">Remarks</span></span>  
 <span data-ttu-id="6592d-114">Metody [IHostTaskManager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) i [IHostTaskManager:: SwitchToTask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) przyjmują parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="6592d-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6592d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6592d-115">Requirements</span></span>  
 <span data-ttu-id="6592d-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6592d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6592d-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6592d-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6592d-118">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6592d-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6592d-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6592d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6592d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6592d-120">See also</span></span>

- [<span data-ttu-id="6592d-121">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6592d-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
