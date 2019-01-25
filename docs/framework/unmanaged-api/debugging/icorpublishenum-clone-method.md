---
title: ICorPublishEnum::Clone — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdc8c274cd6949977b3e0ad5df8e1e14692ad167
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563590"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="d30d7-102">ICorPublishEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="d30d7-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="d30d7-103">Tworzy kopię [icorpublishenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d30d7-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d30d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d30d7-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d30d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d30d7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d30d7-106">[out] Wskaźnik na adres `ICorPublishEnum` obiektu, który jest kopią tego `ICorPublishEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d30d7-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d30d7-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d30d7-107">Requirements</span></span>  
 <span data-ttu-id="d30d7-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d30d7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d30d7-109">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d30d7-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d30d7-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d30d7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d30d7-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d30d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30d7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d30d7-112">See also</span></span>
- [<span data-ttu-id="d30d7-113">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="d30d7-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
