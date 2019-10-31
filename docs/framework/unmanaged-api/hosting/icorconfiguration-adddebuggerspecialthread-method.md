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
ms.openlocfilehash: c5d6cfa3826667514eb70f9bb0df118d9ba0d07c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127819"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="13b00-102">ICorConfiguration::AddDebuggerSpecialThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="13b00-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="13b00-103">Wskazuje usługi debugowania, które mogą kontynuować wykonywanie określonego wątku, podczas gdy debuger ma aplikację zatrzymaną w scenariuszach debugowania zarządzanego lub niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="13b00-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13b00-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13b00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13b00-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="13b00-106">podczas Identyfikator wątku, który powinien być dozwolony do dalszego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13b00-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13b00-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13b00-107">Remarks</span></span>  
 <span data-ttu-id="13b00-108">Określony wątek nie będzie mógł uruchamiać kodu zarządzanego lub wprowadzać środowiska uruchomieniowego w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="13b00-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="13b00-109">Przykładem takiego wątku będzie wątek w procesie do obsługi starszych debugerów skryptów.</span><span class="sxs-lookup"><span data-stu-id="13b00-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13b00-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13b00-110">Requirements</span></span>  
 <span data-ttu-id="13b00-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13b00-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13b00-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13b00-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13b00-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="13b00-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13b00-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13b00-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b00-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13b00-115">See also</span></span>

- [<span data-ttu-id="13b00-116">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="13b00-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
