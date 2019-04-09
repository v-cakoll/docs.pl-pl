---
title: ICorConfiguration — Interfejs
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24e278b3449d0e17377495cef0f445c1ebed734
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149815"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="4c569-102">ICorConfiguration — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4c569-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="4c569-103">Udostępnia metody do konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="4c569-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c569-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4c569-104">Methods</span></span>  
  
|<span data-ttu-id="4c569-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4c569-105">Method</span></span>|<span data-ttu-id="4c569-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4c569-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c569-107">AddDebuggerSpecialThread, metoda</span><span class="sxs-lookup"><span data-stu-id="4c569-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="4c569-108">Do debugowania usług wskazuje, że określonego wątku powinny mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w zarządzanych lub niezarządzanych scenariusze debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c569-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="4c569-109">SetDebuggerThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="4c569-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="4c569-110">Określa interfejs wywołania zwrotnego, który będzie dzwonić, usług debugowania do debugowania wątków CLR są zablokowane i odblokowane.</span><span class="sxs-lookup"><span data-stu-id="4c569-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="4c569-111">SetGCHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="4c569-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="4c569-112">Określa interfejs wywołania zwrotnego do użycia przez moduł zbierający elementy bezużyteczne na żądanie hosta, aby zmienić limity pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="4c569-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="4c569-113">SetGCThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="4c569-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="4c569-114">Określa interfejs wywołania zwrotnego, planowanie wątków dla zadań innych niż środowiska uruchomieniowego, które w przeciwnym razie zostałby zablokowany dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4c569-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c569-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c569-115">Requirements</span></span>  
 <span data-ttu-id="4c569-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c569-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c569-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c569-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c569-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c569-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="4c569-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4c569-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4c569-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c569-120">See also</span></span>

- [<span data-ttu-id="4c569-121">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4c569-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4c569-122">CorRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="4c569-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
