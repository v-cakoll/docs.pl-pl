---
title: ICorThreadpool::CorChangeTimer — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de4a61f188bc6419b52f168c8bbbf43ad91fa19e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159604"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="672b8-102">ICorThreadpool::CorChangeTimer — Metoda</span><span class="sxs-lookup"><span data-stu-id="672b8-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="672b8-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="672b8-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="672b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="672b8-104">Syntax</span></span>  
  
```  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,   
    [in]  ULONG  DueTime,   
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="672b8-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="672b8-105">Requirements</span></span>  
 <span data-ttu-id="672b8-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="672b8-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="672b8-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="672b8-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="672b8-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="672b8-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="672b8-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="672b8-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672b8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="672b8-110">See also</span></span>

- [<span data-ttu-id="672b8-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="672b8-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
