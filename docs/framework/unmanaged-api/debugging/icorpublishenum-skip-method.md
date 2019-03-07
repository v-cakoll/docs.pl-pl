---
title: ICorPublishEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f56792bbdf11c099205efd0cb35e3bf02d67632
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466612"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="15870-102">ICorPublishEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="15870-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="15870-103">Przesuwa kursor do przodu w wyliczeniu przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="15870-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15870-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15870-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15870-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15870-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="15870-106">[in] Liczba elementów, o którą należy przesunąć kursor do przodu.</span><span class="sxs-lookup"><span data-stu-id="15870-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15870-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15870-107">Requirements</span></span>  
 <span data-ttu-id="15870-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15870-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15870-109">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="15870-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="15870-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15870-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15870-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15870-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15870-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15870-112">See also</span></span>
- [<span data-ttu-id="15870-113">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="15870-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
