---
title: "WAIT_OPTION — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAIT_OPTION
api_location: mscoree.dll
api_type: COM
f1_keywords: WAIT_OPTION
helpviewer_keywords: WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08bdfc928c56d144f50399814a81795fea74574a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="f9bca-102">WAIT_OPTION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f9bca-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="f9bca-103">Zawiera wartości, które wskazują, że akcja hosta może pobierać operacji wymaganej przez wspólne bloki środowiska uruchomieniowego (języka wspólnego CLR) języka.</span><span class="sxs-lookup"><span data-stu-id="f9bca-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9bca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9bca-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="f9bca-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f9bca-105">Members</span></span>  
  
|<span data-ttu-id="f9bca-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f9bca-106">Member</span></span>|<span data-ttu-id="f9bca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f9bca-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="f9bca-108">Powiadamia hosta, czy zadanie powinno wznowione wywołuje CLR [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f9bca-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="f9bca-109">Powiadamia hosta, że musi on pompa wiadomości w bieżącym wątku systemu operacyjnego, jeśli wątek zostanie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="f9bca-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="f9bca-110">Środowisko uruchomieniowe określa tę wartość tylko dla <xref:System.Threading.ApartmentState.STA> wątku.</span><span class="sxs-lookup"><span data-stu-id="f9bca-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="f9bca-111">Powiadamia hosta, że nie mogą być podzielone żądanie synchronizacji określonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="f9bca-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="f9bca-112">Oznacza to, że host nie może zwracać `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="f9bca-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9bca-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9bca-113">Remarks</span></span>  
 <span data-ttu-id="f9bca-114">[IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) i [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody zarówno przyjmują parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="f9bca-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9bca-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9bca-115">Requirements</span></span>  
 <span data-ttu-id="f9bca-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9bca-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9bca-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9bca-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9bca-118">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f9bca-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9bca-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9bca-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bca-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9bca-120">See Also</span></span>  
 [<span data-ttu-id="f9bca-121">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f9bca-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
