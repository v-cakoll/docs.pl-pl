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
ms.openlocfilehash: 098c23dd0ddff4342aa4cefbaa4e149ed95a1cb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700075"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="20e67-102">ICorThreadpool::CorDeleteTimer — Metoda</span><span class="sxs-lookup"><span data-stu-id="20e67-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="20e67-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="20e67-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e67-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20e67-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="20e67-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20e67-105">Requirements</span></span>  
 <span data-ttu-id="20e67-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e67-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e67-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20e67-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20e67-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20e67-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20e67-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e67-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e67-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20e67-110">See also</span></span>

- [<span data-ttu-id="20e67-111">ICorThreadpool, interfejs</span><span class="sxs-lookup"><span data-stu-id="20e67-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
