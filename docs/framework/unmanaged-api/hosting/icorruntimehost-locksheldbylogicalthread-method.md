---
title: ICorRuntimeHost::LocksHeldByLogicalThread — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90af015de4428f75330de89978a7fc0a4b26750b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144199"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="15e35-102">ICorRuntimeHost::LocksHeldByLogicalThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="15e35-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="15e35-103">Pobiera liczbę blokad, które zawiera bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="15e35-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="15e35-104">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="15e35-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e35-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="15e35-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15e35-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="15e35-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="15e35-107">[out] Wskaźnik z liczbą blokad, które zawiera bieżący wątek.</span><span class="sxs-lookup"><span data-stu-id="15e35-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e35-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15e35-108">Requirements</span></span>  
 <span data-ttu-id="15e35-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e35-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e35-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15e35-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15e35-111">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15e35-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15e35-112">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="15e35-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e35-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15e35-113">See also</span></span>

- [<span data-ttu-id="15e35-114">ICorRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="15e35-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
