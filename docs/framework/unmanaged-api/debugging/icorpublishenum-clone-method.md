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
ms.openlocfilehash: e0ce1d8c0074f62d35e16465b368269e233a713b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993528"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="a86f0-102">ICorPublishEnum::Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="a86f0-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="a86f0-103">Tworzy kopię [icorpublishenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="a86f0-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a86f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a86f0-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a86f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a86f0-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a86f0-106">[out] Wskaźnik na adres `ICorPublishEnum` obiektu, który jest kopią tego `ICorPublishEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a86f0-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a86f0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a86f0-107">Requirements</span></span>  
 <span data-ttu-id="a86f0-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a86f0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a86f0-109">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="a86f0-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a86f0-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a86f0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a86f0-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a86f0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86f0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a86f0-112">See also</span></span>

- [<span data-ttu-id="a86f0-113">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a86f0-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
