---
title: "ICorPublishAppDomainEnum::Next — Metoda"
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
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c9823c0e4a471a398285c5960f3ce7bfc60fb23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="cbace-102">ICorPublishAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="cbace-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="cbace-103">Pobiera określoną liczbę domen aplikacji, które obecnie istnieją w procesie, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="cbace-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbace-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbace-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbace-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbace-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="cbace-106">[in] Liczba elementów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="cbace-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="cbace-107">[out] Wskaźnik do tablicy pobrać [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) obiektów, z których każdy reprezentuje domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cbace-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="cbace-108">[out] Wskaźnik do liczby domen aplikacji faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="cbace-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="cbace-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="cbace-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbace-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbace-110">Requirements</span></span>  
 <span data-ttu-id="cbace-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbace-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbace-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="cbace-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cbace-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbace-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbace-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbace-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbace-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbace-115">See Also</span></span>  
 [<span data-ttu-id="cbace-116">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbace-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
