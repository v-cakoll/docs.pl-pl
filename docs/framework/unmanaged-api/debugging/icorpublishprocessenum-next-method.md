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
ms.openlocfilehash: 169716d1a6d0dd633821cc832de96c9a02958d76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183108"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="713aa-102">ICorPublishProcessEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="713aa-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="713aa-103">Pobiera określoną liczbę procesów z kolekcji, począwszy od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="713aa-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="713aa-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="713aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="713aa-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="713aa-106">[in] Liczba procesów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="713aa-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="713aa-107">[out] Wskaźnik do tablicy pobrać [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) obiektów, z których każdy reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="713aa-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="713aa-108">[out] Wskaźnik do liczby procesów rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="713aa-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="713aa-109">Ta wartość może mieć wartości null Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="713aa-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="713aa-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="713aa-110">Requirements</span></span>  
 <span data-ttu-id="713aa-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="713aa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="713aa-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="713aa-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="713aa-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="713aa-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="713aa-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="713aa-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="713aa-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="713aa-115">See also</span></span>

- [<span data-ttu-id="713aa-116">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="713aa-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
