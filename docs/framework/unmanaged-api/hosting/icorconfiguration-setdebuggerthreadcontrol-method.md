---
title: ICorConfiguration::SetDebuggerThreadControl — Metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fc141cbebe08f8d0974788409d5aef0f68d2878
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205124"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="bd912-102">ICorConfiguration::SetDebuggerThreadControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd912-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="bd912-103">Ustawia interfejs wywołania zwrotnego, że usług debugowania wywoła jako środowisko uruchomieniowe języka wspólnego wątków (CLR) są zablokowane i odblokowany do debugowania.</span><span class="sxs-lookup"><span data-stu-id="bd912-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd912-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd912-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd912-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd912-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="bd912-106">[in] Wskaźnik do [idebuggerthreadcontrol —](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) obiektu, która powiadamia hosta, dotyczące blokowania i odblokowywania wątków przez usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="bd912-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd912-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd912-107">Requirements</span></span>  
 <span data-ttu-id="bd912-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd912-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd912-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bd912-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd912-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd912-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="bd912-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bd912-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd912-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd912-112">See also</span></span>

- [<span data-ttu-id="bd912-113">ICorConfiguration — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bd912-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
