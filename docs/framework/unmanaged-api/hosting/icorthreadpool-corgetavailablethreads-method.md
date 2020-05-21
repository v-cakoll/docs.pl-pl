---
title: ICorThreadpool::CorGetAvailableThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
ms.openlocfilehash: e5c11cfe21303aca6b867951ad610cddc58a0f03
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762763"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="f5b5e-102">ICorThreadpool::CorGetAvailableThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5b5e-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="f5b5e-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f5b5e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5b5e-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f5b5e-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5b5e-105">Requirements</span></span>  
 <span data-ttu-id="f5b5e-106">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5b5e-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b5e-107">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5b5e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5b5e-108">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5b5e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5b5e-109">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b5e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b5e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5b5e-110">See also</span></span>

- [<span data-ttu-id="f5b5e-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5b5e-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
