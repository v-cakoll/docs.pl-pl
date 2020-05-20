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
ms.openlocfilehash: c5ac38005410ae6ed9c2f4160e926987791ad604
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421218"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="8cbe8-102">ICorPublishAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="8cbe8-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="8cbe8-103">Pobiera określoną liczbę domen aplikacji, które aktualnie istnieją w procesie, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="8cbe8-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbe8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cbe8-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cbe8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cbe8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8cbe8-106">podczas Liczba elementów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="8cbe8-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="8cbe8-107">określoną Wskaźnik do tablicy pobranych obiektów [ICorPublishAppDomain](icorpublishappdomain-interface.md) , z których każdy reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cbe8-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8cbe8-108">określoną Wskaźnik na liczbę domen aplikacji, które faktycznie zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="8cbe8-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="8cbe8-109">Ta wartość może być równa null, jeśli `celt` jest taka.</span><span class="sxs-lookup"><span data-stu-id="8cbe8-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cbe8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cbe8-110">Requirements</span></span>  
 <span data-ttu-id="8cbe8-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cbe8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cbe8-112">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="8cbe8-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8cbe8-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8cbe8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cbe8-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cbe8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbe8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cbe8-115">See also</span></span>

- [<span data-ttu-id="8cbe8-116">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8cbe8-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
