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
ms.openlocfilehash: 59b940c0dbe9462dda513e933b7360ff55a9b447
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437352"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="9bb1e-102">ICorConfiguration::AddDebuggerSpecialThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="9bb1e-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="9bb1e-103">Do debugowania usług wskazuje, że określonego wątku powinien mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w scenariuszach debugowania zarządzanych lub niezarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9bb1e-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb1e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9bb1e-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bb1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9bb1e-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="9bb1e-106">[in] Identyfikator wątku, który powinien mieć możliwość kontynuowania wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9bb1e-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bb1e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bb1e-107">Remarks</span></span>  
 <span data-ttu-id="9bb1e-108">Określony wątek będzie nie można uruchamiać kodu zarządzanego lub wprowadź środowiska uruchomieniowego w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="9bb1e-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="9bb1e-109">Przykładem takich wątku może być wątek w trakcie obsługi debugery starszych skryptu.</span><span class="sxs-lookup"><span data-stu-id="9bb1e-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bb1e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bb1e-110">Requirements</span></span>  
 <span data-ttu-id="9bb1e-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bb1e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bb1e-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9bb1e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bb1e-113">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bb1e-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bb1e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bb1e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb1e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bb1e-115">See Also</span></span>  
 [<span data-ttu-id="9bb1e-116">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="9bb1e-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
