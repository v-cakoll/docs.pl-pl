---
title: ICorPublishAppDomainEnum::Next — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 0553d8b07e3a16dc31474b5470ba2dd8ba365cb2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140503"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="b1cf0-102">ICorPublishAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1cf0-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="b1cf0-103">Pobiera określoną liczbę domen aplikacji, które aktualnie istnieją w procesie, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="b1cf0-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1cf0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1cf0-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1cf0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1cf0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b1cf0-106">podczas Liczba elementów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="b1cf0-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="b1cf0-107">określoną Wskaźnik do tablicy pobranych obiektów [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) , z których każdy reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1cf0-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b1cf0-108">określoną Wskaźnik na liczbę domen aplikacji, które faktycznie zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="b1cf0-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="b1cf0-109">Ta wartość może być równa null, jeśli `celt` to jeden.</span><span class="sxs-lookup"><span data-stu-id="b1cf0-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1cf0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1cf0-110">Requirements</span></span>  
 <span data-ttu-id="b1cf0-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1cf0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1cf0-112">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b1cf0-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b1cf0-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1cf0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1cf0-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1cf0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cf0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1cf0-115">See also</span></span>

- [<span data-ttu-id="b1cf0-116">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1cf0-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
