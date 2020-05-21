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
ms.openlocfilehash: 3b8c9421dea4040a9f183b886f1ad8575cace780
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762435"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="3f00f-102">ICorConfiguration — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f00f-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="3f00f-103">Zapewnia metody konfigurowania środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="3f00f-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f00f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3f00f-104">Methods</span></span>  
  
|<span data-ttu-id="3f00f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f00f-105">Method</span></span>|<span data-ttu-id="3f00f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3f00f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f00f-107">AddDebuggerSpecialThread, metoda</span><span class="sxs-lookup"><span data-stu-id="3f00f-107">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="3f00f-108">Wskazuje usługi debugowania, które mogą kontynuować wykonywanie określonego wątku, podczas gdy debuger ma aplikację zatrzymaną w scenariuszach debugowania zarządzanego lub niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3f00f-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="3f00f-109">SetDebuggerThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="3f00f-109">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="3f00f-110">Ustawia interfejs wywołania zwrotnego, który będzie wywoływany przez usługi debugowania, gdy wątki CLR są blokowane i odblokowywane w celu debugowania.</span><span class="sxs-lookup"><span data-stu-id="3f00f-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="3f00f-111">SetGCHostControl, metoda</span><span class="sxs-lookup"><span data-stu-id="3f00f-111">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="3f00f-112">Ustawia interfejs wywołania zwrotnego, który ma być używany przez moduł wyrzucania elementów bezużytecznych, aby zażądać od hosta zmiany limitów pamięci wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="3f00f-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="3f00f-113">SetGCThreadControl, metoda</span><span class="sxs-lookup"><span data-stu-id="3f00f-113">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="3f00f-114">Ustawia interfejs wywołania zwrotnego dla wątków planowania dla zadań innych niż środowisko uruchomieniowe, które w przeciwnym razie byłyby blokowane dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="3f00f-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f00f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f00f-115">Requirements</span></span>  
 <span data-ttu-id="3f00f-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f00f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f00f-117">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3f00f-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f00f-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3f00f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f00f-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f00f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f00f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f00f-120">See also</span></span>

- [<span data-ttu-id="3f00f-121">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3f00f-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3f00f-122">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="3f00f-122">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
