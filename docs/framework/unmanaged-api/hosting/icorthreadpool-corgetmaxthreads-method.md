---
title: ICorThreadpool::CorGetMaxThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: 46ffdb21c1f3b501cc28afffc224349887af5644
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762754"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="e4754-102">ICorThreadpool::CorGetMaxThreads — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4754-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="e4754-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e4754-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4754-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4754-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e4754-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4754-105">Requirements</span></span>  
 <span data-ttu-id="e4754-106">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4754-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4754-107">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4754-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4754-108">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4754-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4754-109">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4754-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4754-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4754-110">See also</span></span>

- [<span data-ttu-id="e4754-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4754-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
