---
title: EClrEvent — Wyliczenie
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d79b0c1fed0178f8463174fe981f250d6f6fb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430710"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="9a06c-102">EClrEvent — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9a06c-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="9a06c-103">W tym artykule opisano typowe zdarzenia środowiska uruchomieniowego (języka wspólnego CLR) języka, dla których hosta można zarejestrować wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="9a06c-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a06c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a06c-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="9a06c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9a06c-105">Members</span></span>  
  
|<span data-ttu-id="9a06c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9a06c-106">Member</span></span>|<span data-ttu-id="9a06c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9a06c-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="9a06c-108">Określa krytyczny błąd środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9a06c-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="9a06c-109">Określa zwalnianie określonego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9a06c-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="9a06c-110">Określa wygenerowania wiadomości zarządzane debugowania Asystenta (MDA).</span><span class="sxs-lookup"><span data-stu-id="9a06c-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="9a06c-111">Określa, że wystąpił błąd przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="9a06c-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a06c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a06c-112">Remarks</span></span>  
 <span data-ttu-id="9a06c-113">Hosta można zarejestrować wywołań zwrotnych dla każdego z typów zdarzeń opisanego przez `EClrEvent` przez wywołanie metody [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9a06c-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="9a06c-114">Host pobiera wskaźnik do tego interfejsu, wywołując [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9a06c-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="9a06c-115">`Event_CLRDisabled` i `Event_DomainUnload` zdarzenia można podnieść więcej niż jeden raz i inne wątki sygnalizują zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9a06c-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="9a06c-116">`Event_MDAFired` Tworzenie wywołuje zdarzenie [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) wystąpienia, które zawiera szczegóły komunikat MDA.</span><span class="sxs-lookup"><span data-stu-id="9a06c-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="9a06c-117">Aby uzyskać więcej informacji o mda, zobacz [diagnozowanie problemów z Asystenci zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="9a06c-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a06c-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a06c-118">Requirements</span></span>  
 <span data-ttu-id="9a06c-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a06c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a06c-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a06c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a06c-121">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a06c-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a06c-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a06c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a06c-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a06c-123">See Also</span></span>  
 [<span data-ttu-id="9a06c-124">IActionOnCLREvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a06c-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="9a06c-125">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a06c-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9a06c-126">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9a06c-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
