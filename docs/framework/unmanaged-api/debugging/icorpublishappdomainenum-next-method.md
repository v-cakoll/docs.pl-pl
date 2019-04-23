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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14d364320c82f061ef606a402563dacfce28139
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186241"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="fc634-102">ICorPublishAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc634-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="fc634-103">Pobiera określoną liczbę domen aplikacji, które obecnie istnieją w procesie, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="fc634-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc634-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc634-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc634-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc634-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fc634-106">[in] Liczba elementów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="fc634-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="fc634-107">[out] Wskaźnik do tablicy pobrać [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) obiektów, z których każdy reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fc634-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fc634-108">[out] Wskaźnik do liczby domen aplikacji rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="fc634-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="fc634-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="fc634-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc634-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc634-110">Requirements</span></span>  
 <span data-ttu-id="fc634-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc634-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc634-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="fc634-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fc634-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc634-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc634-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc634-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc634-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc634-115">See also</span></span>

- [<span data-ttu-id="fc634-116">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc634-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
