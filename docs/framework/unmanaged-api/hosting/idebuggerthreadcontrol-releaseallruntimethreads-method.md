---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 50ffb33456f942a71089f9bc44daa07f6b77ab21
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805296"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="c5fda-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5fda-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="c5fda-103">Powiadamia hosta o wydaniu wszystkich zablokowanych wątków przez usługi debugowania.</span><span class="sxs-lookup"><span data-stu-id="c5fda-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5fda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5fda-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c5fda-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5fda-105">Remarks</span></span>  
 <span data-ttu-id="c5fda-106">`ReleaseAllRuntimeThreads`Metoda nigdy nie będzie wywoływana w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c5fda-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="c5fda-107">Jeśli host ma zablokowany wątek uruchomieniowy, powinien go teraz wydać.</span><span class="sxs-lookup"><span data-stu-id="c5fda-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5fda-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5fda-108">Requirements</span></span>  
 <span data-ttu-id="c5fda-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5fda-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5fda-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c5fda-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5fda-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c5fda-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5fda-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5fda-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fda-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5fda-113">See also</span></span>

- [<span data-ttu-id="c5fda-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="c5fda-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
