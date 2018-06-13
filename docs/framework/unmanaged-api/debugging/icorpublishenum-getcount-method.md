---
title: ICorPublishEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f191c31ec5333fbea52c298f477c8c624beb92b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424511"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="db865-102">ICorPublishEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="db865-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="db865-103">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="db865-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db865-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db865-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db865-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db865-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="db865-106">[out] Wskaźnik do liczby elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="db865-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db865-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db865-107">Requirements</span></span>  
 <span data-ttu-id="db865-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db865-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db865-109">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="db865-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="db865-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db865-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db865-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db865-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db865-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db865-112">See Also</span></span>  
 [<span data-ttu-id="db865-113">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="db865-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
