---
title: ICorConfiguration::AddDebuggerSpecialThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 067765fbf500b2d20d84273d8df70c8e05a6ddc4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485903"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="e898e-102">ICorConfiguration::AddDebuggerSpecialThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="e898e-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="e898e-103">Do debugowania usług wskazuje, że określonego wątku powinny mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w zarządzanych lub niezarządzanych scenariusze debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e898e-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e898e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e898e-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e898e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e898e-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="e898e-106">[in] Identyfikator wątku, który powinien być dozwolony kontynuowania wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e898e-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e898e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e898e-107">Remarks</span></span>  
 <span data-ttu-id="e898e-108">Do uruchomienia kodu zarządzanego, lub wprowadź środowiska uruchomieniowego w żaden sposób nie będzie można określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="e898e-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="e898e-109">Przykładem takiego wątku może być wątek w trakcie obsługi debugery starszej wersji skryptu.</span><span class="sxs-lookup"><span data-stu-id="e898e-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e898e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e898e-110">Requirements</span></span>  
 <span data-ttu-id="e898e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e898e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e898e-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e898e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e898e-113">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e898e-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e898e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e898e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e898e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e898e-115">See also</span></span>
- [<span data-ttu-id="e898e-116">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="e898e-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
