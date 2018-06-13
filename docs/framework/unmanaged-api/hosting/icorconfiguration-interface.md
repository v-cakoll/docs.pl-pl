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
ms.openlocfilehash: 63699f0af69b3a7623c5e9da156c2ff8ae83ccfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437527"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="c9c18-102">ICorConfiguration — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c9c18-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="c9c18-103">Udostępnia metody konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c9c18-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9c18-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c9c18-104">Methods</span></span>  
  
|<span data-ttu-id="c9c18-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c9c18-105">Method</span></span>|<span data-ttu-id="c9c18-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c9c18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9c18-107">AddDebuggerSpecialThread, metoda</span><span class="sxs-lookup"><span data-stu-id="c9c18-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="c9c18-108">Do debugowania usług wskazuje, że określonego wątku powinien mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w scenariuszach debugowania zarządzanych lub niezarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9c18-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="c9c18-109">SetDebuggerThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="c9c18-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="c9c18-110">Określa interfejs wywołania zwrotnego, który usług debugowania wywoła wątków CLR są zablokowane i odblokowany do debugowania.</span><span class="sxs-lookup"><span data-stu-id="c9c18-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="c9c18-111">SetGCHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="c9c18-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="c9c18-112">Ustawia wywołanie zwrotne interfejsu używanego przez moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="c9c18-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="c9c18-113">SetGCThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="c9c18-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="c9c18-114">Określa interfejs wywołania zwrotnego dla planowania wątków dla zadań z systemem innym niż środowisko uruchomieniowe, które można zablokować dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c9c18-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9c18-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9c18-115">Requirements</span></span>  
 <span data-ttu-id="c9c18-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9c18-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9c18-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9c18-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9c18-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9c18-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9c18-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9c18-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c18-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9c18-120">See Also</span></span>  
 [<span data-ttu-id="c9c18-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c9c18-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c9c18-122">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="c9c18-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
