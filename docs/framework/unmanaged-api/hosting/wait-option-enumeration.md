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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ac28f28d4d284ba26fadd46e53ebeb8e5b5f3cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139584"
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="7a95e-102">WAIT_OPTION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7a95e-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="7a95e-103">Zawiera wartości, które wskazują, że akcja hosta powinno zająć, jeśli operacji wymaganej przez bloki języka, aby środowisko uruchomieniowe (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="7a95e-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a95e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a95e-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="7a95e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7a95e-105">Members</span></span>  
  
|<span data-ttu-id="7a95e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7a95e-106">Member</span></span>|<span data-ttu-id="7a95e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7a95e-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="7a95e-108">Powiadamia hosta, że zadanie powinno wznowione, jeśli środowisko CLR wywołuje [ihosttask::alert —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7a95e-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="7a95e-109">Powiadamia hosta, należy go pompy komunikatów dla bieżącego wątku systemu operacyjnego Jeśli wątek zostanie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="7a95e-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="7a95e-110">Środowisko wykonawcze określa tę wartość tylko na <xref:System.Threading.ApartmentState.STA> wątku.</span><span class="sxs-lookup"><span data-stu-id="7a95e-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="7a95e-111">Powiadamia hosta, że żądanie synchronizacji określonego nie można podzielić przez hosta.</span><span class="sxs-lookup"><span data-stu-id="7a95e-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="7a95e-112">Oznacza to, że host nie może zwracać `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="7a95e-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a95e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a95e-113">Remarks</span></span>  
 <span data-ttu-id="7a95e-114">[Ihosttaskmanager::Sleep —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) i [ihosttaskmanager::switchtotask —](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody przyjmować parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="7a95e-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a95e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a95e-115">Requirements</span></span>  
 <span data-ttu-id="7a95e-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a95e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a95e-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7a95e-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7a95e-118">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a95e-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a95e-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a95e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a95e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a95e-120">See also</span></span>

- [<span data-ttu-id="7a95e-121">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7a95e-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
