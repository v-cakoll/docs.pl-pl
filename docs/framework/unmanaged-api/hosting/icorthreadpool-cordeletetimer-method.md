---
title: ICorThreadpool::CorDeleteTimer — Metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7cba6db456d15ebcfedb305343962b37e5ca1a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491964"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="50b20-102">ICorThreadpool::CorDeleteTimer — Metoda</span><span class="sxs-lookup"><span data-stu-id="50b20-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="50b20-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50b20-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50b20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50b20-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="50b20-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50b20-105">Requirements</span></span>  
 <span data-ttu-id="50b20-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50b20-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50b20-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50b20-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50b20-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50b20-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50b20-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50b20-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b20-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50b20-110">See also</span></span>
- [<span data-ttu-id="50b20-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="50b20-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
