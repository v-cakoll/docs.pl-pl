---
title: "ICorPublishAppDomainEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79b9ad5711ac1d0166a7ad328cc227f17780476c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="1abc9-102">ICorPublishAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="1abc9-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="1abc9-103">Pobiera określoną liczbę domen aplikacji, które obecnie istnieją w procesie, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="1abc9-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1abc9-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1abc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1abc9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1abc9-106">[in] Liczba elementów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="1abc9-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="1abc9-107">[out] Wskaźnik do tablicy pobrać [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) obiektów, z których każdy reprezentuje domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1abc9-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1abc9-108">[out] Wskaźnik do liczby domen aplikacji faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="1abc9-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="1abc9-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="1abc9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1abc9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1abc9-110">Requirements</span></span>  
 <span data-ttu-id="1abc9-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1abc9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1abc9-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="1abc9-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1abc9-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1abc9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1abc9-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1abc9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abc9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1abc9-115">See Also</span></span>  
 [<span data-ttu-id="1abc9-116">ICorPublishAppDomainEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="1abc9-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
