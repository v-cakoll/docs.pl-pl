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
ms.openlocfilehash: 0f6a369691ab2e4e9fd2e5d9731fb1dc0a42ba11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127794"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="92364-102">ICorConfiguration::SetDebuggerThreadControl — Metoda</span><span class="sxs-lookup"><span data-stu-id="92364-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="92364-103">Ustawia interfejs wywołania zwrotnego, który będzie wywoływany przez usługi debugowania jako wątki środowiska uruchomieniowego języka wspólnego (CLR), które są blokowane i odblokowywane na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="92364-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92364-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92364-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92364-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92364-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="92364-106">podczas Wskaźnik do obiektu [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) , który powiadamia hosta o blokowaniu i odblokowywaniu wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="92364-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92364-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92364-107">Requirements</span></span>  
 <span data-ttu-id="92364-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92364-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92364-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92364-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92364-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92364-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92364-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92364-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92364-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92364-112">See also</span></span>

- [<span data-ttu-id="92364-113">ICorConfiguration, interfejs</span><span class="sxs-lookup"><span data-stu-id="92364-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
