---
title: ICorPublishProcessEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19a10a527c37d93d00bec799fdaa12bb0ad3fdbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423874"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="1458e-102">ICorPublishProcessEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="1458e-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="1458e-103">Pobiera określoną liczbę procesów z kolekcji, począwszy od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="1458e-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1458e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1458e-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1458e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1458e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="1458e-106">[in] Liczba procesów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="1458e-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="1458e-107">[out] Wskaźnik do tablicy pobrać [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) obiektów, z których każdy reprezentuje procesu.</span><span class="sxs-lookup"><span data-stu-id="1458e-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="1458e-108">[out] Wskaźnik do liczby procesów faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="1458e-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="1458e-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="1458e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1458e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1458e-110">Requirements</span></span>  
 <span data-ttu-id="1458e-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1458e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1458e-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="1458e-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1458e-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1458e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1458e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1458e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1458e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1458e-115">See Also</span></span>  
 [<span data-ttu-id="1458e-116">ICorPublishProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="1458e-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
