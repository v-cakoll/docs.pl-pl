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
ms.openlocfilehash: a691f61fcd25b7aaaae90e6adcc3c2ee0c421cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="a532a-102">ICorPublishEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="a532a-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="a532a-103">Przesuwa kursor do przodu w wyliczeniu określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="a532a-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a532a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a532a-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a532a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a532a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a532a-106">[in] Liczba elementów, o którą należy przesunąć kursor do przodu.</span><span class="sxs-lookup"><span data-stu-id="a532a-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a532a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a532a-107">Requirements</span></span>  
 <span data-ttu-id="a532a-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a532a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a532a-109">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a532a-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a532a-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a532a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a532a-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a532a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a532a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a532a-112">See Also</span></span>  
 [<span data-ttu-id="a532a-113">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a532a-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
