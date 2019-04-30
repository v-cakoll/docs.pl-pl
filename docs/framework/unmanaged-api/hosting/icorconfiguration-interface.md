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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763279"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="721ec-102">ICorConfiguration — Interfejs</span><span class="sxs-lookup"><span data-stu-id="721ec-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="721ec-103">Udostępnia metody do konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="721ec-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="721ec-104">Metody</span><span class="sxs-lookup"><span data-stu-id="721ec-104">Methods</span></span>  
  
|<span data-ttu-id="721ec-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="721ec-105">Method</span></span>|<span data-ttu-id="721ec-106">Opis</span><span class="sxs-lookup"><span data-stu-id="721ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="721ec-107">AddDebuggerSpecialThread, metoda</span><span class="sxs-lookup"><span data-stu-id="721ec-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="721ec-108">Do debugowania usług wskazuje, że określonego wątku powinny mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w zarządzanych lub niezarządzanych scenariusze debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="721ec-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="721ec-109">SetDebuggerThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="721ec-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="721ec-110">Określa interfejs wywołania zwrotnego, który będzie dzwonić, usług debugowania do debugowania wątków CLR są zablokowane i odblokowane.</span><span class="sxs-lookup"><span data-stu-id="721ec-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="721ec-111">SetGCHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="721ec-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="721ec-112">Określa interfejs wywołania zwrotnego do użycia przez moduł zbierający elementy bezużyteczne na żądanie hosta, aby zmienić limity pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="721ec-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="721ec-113">SetGCThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="721ec-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="721ec-114">Określa interfejs wywołania zwrotnego, planowanie wątków dla zadań innych niż środowiska uruchomieniowego, które w przeciwnym razie zostałby zablokowany dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="721ec-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="721ec-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="721ec-115">Requirements</span></span>  
 <span data-ttu-id="721ec-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="721ec-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="721ec-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="721ec-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="721ec-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="721ec-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="721ec-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="721ec-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="721ec-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="721ec-120">See also</span></span>

- [<span data-ttu-id="721ec-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="721ec-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="721ec-122">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="721ec-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
