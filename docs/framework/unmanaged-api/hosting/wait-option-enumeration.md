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
ms.openlocfilehash: 2f83bc5b114b746958f936c311efa823d88441d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503890"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="c98c5-102">WAIT_OPTION — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c98c5-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="c98c5-103">Zawiera wartości wskazujące akcję, którą host powinien wykonać, jeśli operacja zażądała bloków środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c98c5-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c98c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c98c5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="c98c5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c98c5-105">Members</span></span>  
  
|<span data-ttu-id="c98c5-106">Członek</span><span class="sxs-lookup"><span data-stu-id="c98c5-106">Member</span></span>|<span data-ttu-id="c98c5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c98c5-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="c98c5-108">Powiadamia hosta, że zadanie powinno zostać wznowione, jeśli środowisko CLR wywoła metodę [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c98c5-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="c98c5-109">Powiadamia hosta, że musi pompować komunikaty w bieżącym wątku systemu operacyjnego, jeśli wątek zostanie zablokowany.</span><span class="sxs-lookup"><span data-stu-id="c98c5-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="c98c5-110">Środowisko uruchomieniowe określa tę wartość tylko w <xref:System.Threading.ApartmentState.STA> wątku.</span><span class="sxs-lookup"><span data-stu-id="c98c5-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="c98c5-111">Powiadamia hosta, że nie można rozbić określonego żądania synchronizacji przez hosta.</span><span class="sxs-lookup"><span data-stu-id="c98c5-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="c98c5-112">Oznacza to, że host nie może zwrócić `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="c98c5-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c98c5-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c98c5-113">Remarks</span></span>  
 <span data-ttu-id="c98c5-114">Metody [IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md) i [IHostTaskManager:: SwitchToTask —](ihosttaskmanager-switchtotask-method.md) przyjmują parametr tego typu.</span><span class="sxs-lookup"><span data-stu-id="c98c5-114">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c98c5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c98c5-115">Requirements</span></span>  
 <span data-ttu-id="c98c5-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c98c5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c98c5-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c98c5-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c98c5-118">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c98c5-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c98c5-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c98c5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98c5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c98c5-120">See also</span></span>

- [<span data-ttu-id="c98c5-121">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c98c5-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
