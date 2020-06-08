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
ms.openlocfilehash: 3ecaebb9d943a3cdbb231307012b5dc3aaf000f7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493421"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="d3fc3-102">EClrEvent — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d3fc3-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="d3fc3-103">Opisuje zdarzenia środowiska uruchomieniowego języka wspólnego (CLR), dla których host może rejestrować wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="d3fc3-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3fc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3fc3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="d3fc3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d3fc3-105">Members</span></span>  
  
|<span data-ttu-id="d3fc3-106">Członek</span><span class="sxs-lookup"><span data-stu-id="d3fc3-106">Member</span></span>|<span data-ttu-id="d3fc3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d3fc3-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="d3fc3-108">Określa krytyczny błąd CLR.</span><span class="sxs-lookup"><span data-stu-id="d3fc3-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="d3fc3-109">Określa wyładowywanie określonego <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="d3fc3-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="d3fc3-110">Określa, że został wygenerowany komunikat Asystent debugowania zarządzanego (MDA).</span><span class="sxs-lookup"><span data-stu-id="d3fc3-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="d3fc3-111">Określa, że wystąpił błąd przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="d3fc3-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3fc3-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3fc3-112">Remarks</span></span>  
 <span data-ttu-id="d3fc3-113">Host może rejestrować wywołania zwrotne dla dowolnego typu zdarzenia opisanego przez `EClrEvent` wywoływanie metod interfejsu [ICLROnEventManager](iclroneventmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d3fc3-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="d3fc3-114">Host Pobiera wskaźnik do tego interfejsu, wywołując metodę [ICLRControl:: GetCLRManager —](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d3fc3-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="d3fc3-115">`Event_CLRDisabled`Zdarzenia i `Event_DomainUnload` mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d3fc3-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="d3fc3-116">`Event_MDAFired`Zdarzenie wywołuje Tworzenie wystąpienia [MDAInfo —](mdainfo-structure.md) zawierającego szczegóły komunikatu MDA.</span><span class="sxs-lookup"><span data-stu-id="d3fc3-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="d3fc3-117">Aby uzyskać więcej informacji na temat MDA, zobacz [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="d3fc3-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3fc3-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3fc3-118">Requirements</span></span>  
 <span data-ttu-id="d3fc3-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3fc3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3fc3-120">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3fc3-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3fc3-121">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3fc3-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3fc3-122">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3fc3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fc3-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3fc3-123">See also</span></span>

- [<span data-ttu-id="d3fc3-124">IActionOnCLREvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3fc3-124">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="d3fc3-125">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3fc3-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d3fc3-126">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d3fc3-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
