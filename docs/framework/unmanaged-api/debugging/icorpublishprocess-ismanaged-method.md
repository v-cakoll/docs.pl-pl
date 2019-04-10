---
title: ICorPublishProcess::IsManaged — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29c5f96bab374d6e2d43424370bff2a4a2ab6df3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218293"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="4a2eb-102">ICorPublishProcess::IsManaged — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a2eb-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="4a2eb-103">Pobiera wartość wskazującą, czy proces odwołuje się ten [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) wiadomo, że masz kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a2eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a2eb-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a2eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a2eb-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="4a2eb-106">[out] Wskaźnik na wartość logiczną, wskazującą, czy kod ma być zarządzany przez proces.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="4a2eb-107">Wartość jest `true` Jeśli proces ma zarządzany kod; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a2eb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a2eb-108">Remarks</span></span>  
 <span data-ttu-id="4a2eb-109">Ponieważ bieżąca wersja `ICorPublishProcess` zezwala na dostęp tylko do procesów, które mają kod zarządzany, `IsManaged` zawsze zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="4a2eb-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a2eb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a2eb-110">Requirements</span></span>  
 <span data-ttu-id="4a2eb-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a2eb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a2eb-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="4a2eb-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4a2eb-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a2eb-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4a2eb-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4a2eb-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4a2eb-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a2eb-115">See also</span></span>

- [<span data-ttu-id="4a2eb-116">ICorPublishProcess — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4a2eb-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
