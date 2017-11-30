---
title: "ICorPublishEnum::Clone — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.Clone
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 607d89f2220f18d58b03b4fdc8a3819e29cdc60d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="76d7e-102">ICorPublishEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="76d7e-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="76d7e-103">Tworzy kopię tego [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="76d7e-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76d7e-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76d7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76d7e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="76d7e-106">[out] Wskaźnik do adresu `ICorPublishEnum` obiektu, który jest kopią tego `ICorPublishEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="76d7e-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76d7e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76d7e-107">Requirements</span></span>  
 <span data-ttu-id="76d7e-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76d7e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76d7e-109">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="76d7e-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="76d7e-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76d7e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76d7e-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76d7e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d7e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76d7e-112">See Also</span></span>  
 [<span data-ttu-id="76d7e-113">ICorPublishEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="76d7e-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
