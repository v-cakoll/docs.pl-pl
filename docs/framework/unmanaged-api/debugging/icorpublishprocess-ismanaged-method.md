---
title: "ICorPublishProcess::IsManaged — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 622781a6c1ad5d5efa3bb2d5227c4f5b845bf94e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="b4ddb-102">ICorPublishProcess::IsManaged — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4ddb-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="b4ddb-103">Pobiera wartość wskazującą, czy proces odwołuje się ten [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) wiadomo, że mają kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b4ddb-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ddb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4ddb-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4ddb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4ddb-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="b4ddb-106">[out] Wskaźnik na wartość logiczną, wskazującą, czy kod ma być zarządzany przez proces.</span><span class="sxs-lookup"><span data-stu-id="b4ddb-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="b4ddb-107">Wartość jest `true` Jeśli proces ma zarządzanego kodu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="b4ddb-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4ddb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4ddb-108">Remarks</span></span>  
 <span data-ttu-id="b4ddb-109">Ponieważ bieżąca wersja `ICorPublishProcess` zezwala na dostęp tylko do procesów, które mają kod zarządzany, `IsManaged` zawsze zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="b4ddb-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ddb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4ddb-110">Requirements</span></span>  
 <span data-ttu-id="b4ddb-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4ddb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ddb-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b4ddb-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b4ddb-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4ddb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4ddb-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ddb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ddb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4ddb-115">See Also</span></span>  
 [<span data-ttu-id="b4ddb-116">ICorPublishProcess — interfejs</span><span class="sxs-lookup"><span data-stu-id="b4ddb-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
