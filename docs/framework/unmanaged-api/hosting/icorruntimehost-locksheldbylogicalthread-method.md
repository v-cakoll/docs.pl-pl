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
ms.openlocfilehash: f6ef7e06d94cb22d266949927cb15105b1602d3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139530"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="e3939-102">ICorRuntimeHost::LocksHeldByLogicalThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3939-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="e3939-103">Pobiera liczbę blokad, które są przechowywane w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="e3939-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="e3939-104">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e3939-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3939-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3939-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3939-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3939-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="e3939-107">określoną Wskaźnik do liczby blokad, które są przechowywane w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="e3939-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3939-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3939-108">Requirements</span></span>  
 <span data-ttu-id="e3939-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3939-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3939-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e3939-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3939-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e3939-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3939-112">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e3939-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3939-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3939-113">See also</span></span>

- [<span data-ttu-id="e3939-114">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3939-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
