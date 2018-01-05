---
title: "ICorConfiguration — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorConfiguration
helpviewer_keywords: ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af9a7d4bb1d38fd4a81e954074b074325409ee5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="05fdc-102">ICorConfiguration — Interfejs</span><span class="sxs-lookup"><span data-stu-id="05fdc-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="05fdc-103">Udostępnia metody konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="05fdc-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05fdc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05fdc-104">Methods</span></span>  
  
|<span data-ttu-id="05fdc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05fdc-105">Method</span></span>|<span data-ttu-id="05fdc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="05fdc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05fdc-107">AddDebuggerSpecialThread, metoda</span><span class="sxs-lookup"><span data-stu-id="05fdc-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="05fdc-108">Do debugowania usług wskazuje, że określonego wątku powinien mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w scenariuszach debugowania zarządzanych lub niezarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05fdc-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="05fdc-109">SetDebuggerThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="05fdc-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="05fdc-110">Określa interfejs wywołania zwrotnego, który usług debugowania wywoła wątków CLR są zablokowane i odblokowany do debugowania.</span><span class="sxs-lookup"><span data-stu-id="05fdc-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="05fdc-111">SetGCHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="05fdc-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="05fdc-112">Ustawia wywołanie zwrotne interfejsu używanego przez moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="05fdc-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="05fdc-113">SetGCThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="05fdc-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="05fdc-114">Określa interfejs wywołania zwrotnego dla planowania wątków dla zadań z systemem innym niż środowisko uruchomieniowe, które można zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="05fdc-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05fdc-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05fdc-115">Requirements</span></span>  
 <span data-ttu-id="05fdc-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05fdc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05fdc-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05fdc-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05fdc-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05fdc-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05fdc-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05fdc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fdc-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05fdc-120">See Also</span></span>  
 [<span data-ttu-id="05fdc-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="05fdc-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="05fdc-122">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="05fdc-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
