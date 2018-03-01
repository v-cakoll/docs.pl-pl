---
title: "ICorRuntimeHost::LocksHeldByLogicalThread — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7875d78415d06a55c11a6b42476ff806a5cadc78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="f8015-102">ICorRuntimeHost::LocksHeldByLogicalThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8015-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="f8015-103">Pobiera liczbę blokad, które przechowuje bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="f8015-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="f8015-104">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f8015-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8015-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8015-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8015-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8015-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="f8015-107">[out] Wskaźnik do liczbę blokad, które przechowuje bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="f8015-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8015-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8015-108">Requirements</span></span>  
 <span data-ttu-id="f8015-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8015-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8015-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8015-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8015-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8015-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8015-112">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f8015-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8015-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8015-113">See Also</span></span>  
 [<span data-ttu-id="f8015-114">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8015-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
