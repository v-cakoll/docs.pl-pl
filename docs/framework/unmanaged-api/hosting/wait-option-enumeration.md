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
ms.openlocfilehash: fb37394799db39baa406ef332066d5ebb2dbf19d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441932"
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="3fe91-102">WAIT_OPTION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3fe91-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="3fe91-103">Zawiera wartości, które wskazują, że akcja hosta może pobierać operacji wymaganej przez wspólne bloki środowiska uruchomieniowego (języka wspólnego CLR) języka.</span><span class="sxs-lookup"><span data-stu-id="3fe91-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fe91-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="3fe91-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3fe91-105">Members</span></span>  
  
|<span data-ttu-id="3fe91-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3fe91-106">Member</span></span>|<span data-ttu-id="3fe91-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3fe91-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="3fe91-108">Powiadamia hosta, czy zadanie powinno wznowione wywołuje CLR [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3fe91-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="3fe91-109">Powiadamia hosta, że musi on pompa wiadomości w bieżącym wątku systemu operacyjnego, jeśli wątek zostanie zablokowane.</span><span class="sxs-lookup"><span data-stu-id="3fe91-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="3fe91-110">Środowisko uruchomieniowe określa tę wartość tylko dla <xref:System.Threading.ApartmentState.STA> wątku.</span><span class="sxs-lookup"><span data-stu-id="3fe91-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="3fe91-111">Powiadamia hosta, że nie mogą być podzielone żądanie synchronizacji określonej przez hosta.</span><span class="sxs-lookup"><span data-stu-id="3fe91-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="3fe91-112">Oznacza to, że host nie może zwracać `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="3fe91-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fe91-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fe91-113">Remarks</span></span>  
 <span data-ttu-id="3fe91-114">[IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) i [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody zarówno przyjmują parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="3fe91-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fe91-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fe91-115">Requirements</span></span>  
 <span data-ttu-id="3fe91-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fe91-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fe91-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3fe91-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fe91-118">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fe91-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fe91-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fe91-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe91-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fe91-120">See Also</span></span>  
 [<span data-ttu-id="3fe91-121">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3fe91-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
