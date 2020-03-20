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
ms.openlocfilehash: 6f7f400c51ded0b98c0c2286cb6f90bbd77e47d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178399"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="71380-102">ICorPublishAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="71380-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="71380-103">Pobiera określoną liczbę domen aplikacji, które obecnie istnieją w procesie, począwszy od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="71380-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71380-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="71380-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71380-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71380-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="71380-106">[w] Liczba elementów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="71380-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="71380-107">[na zewnątrz] Wskaźnik do tablicy pobranych obiektów [ICorPublishAppDomain,](icorpublishappdomain-interface.md) z których każdy reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71380-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="71380-108">[na zewnątrz] Wskaźnik do liczby domen aplikacji faktycznie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="71380-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="71380-109">Ta wartość może `celt` być null, jeśli jest jednym.</span><span class="sxs-lookup"><span data-stu-id="71380-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71380-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71380-110">Requirements</span></span>  
 <span data-ttu-id="71380-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71380-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71380-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="71380-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="71380-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71380-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71380-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71380-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71380-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71380-115">See also</span></span>

- [<span data-ttu-id="71380-116">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="71380-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
