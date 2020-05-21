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
ms.openlocfilehash: 265ab5ae03b7b42c4f5f429df5d659d60e55f18e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760722"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="09526-102">ICorRuntimeHost::LocksHeldByLogicalThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="09526-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="09526-103">Pobiera liczbę blokad, które są przechowywane w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="09526-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="09526-104">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="09526-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09526-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="09526-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09526-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="09526-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="09526-107">określoną Wskaźnik do liczby blokad, które są przechowywane w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="09526-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09526-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09526-108">Requirements</span></span>  
 <span data-ttu-id="09526-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09526-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09526-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="09526-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09526-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="09526-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09526-112">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="09526-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09526-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09526-113">See also</span></span>

- [<span data-ttu-id="09526-114">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="09526-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
