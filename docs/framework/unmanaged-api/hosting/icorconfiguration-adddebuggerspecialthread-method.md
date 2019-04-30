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
ms.openlocfilehash: db1b19c1499f7e8a126933b4d0635a0ab73e72a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763285"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="9a1b5-102">ICorConfiguration::AddDebuggerSpecialThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a1b5-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="9a1b5-103">Do debugowania usług wskazuje, że określonego wątku powinny mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w zarządzanych lub niezarządzanych scenariusze debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a1b5-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a1b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a1b5-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a1b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a1b5-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="9a1b5-106">[in] Identyfikator wątku, który powinien być dozwolony kontynuowania wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9a1b5-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a1b5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a1b5-107">Remarks</span></span>  
 <span data-ttu-id="9a1b5-108">Do uruchomienia kodu zarządzanego, lub wprowadź środowiska uruchomieniowego w żaden sposób nie będzie można określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="9a1b5-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="9a1b5-109">Przykładem takiego wątku może być wątek w trakcie obsługi debugery starszej wersji skryptu.</span><span class="sxs-lookup"><span data-stu-id="9a1b5-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a1b5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a1b5-110">Requirements</span></span>  
 <span data-ttu-id="9a1b5-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a1b5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a1b5-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a1b5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a1b5-113">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a1b5-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a1b5-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a1b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1b5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a1b5-115">See also</span></span>

- [<span data-ttu-id="9a1b5-116">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a1b5-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
