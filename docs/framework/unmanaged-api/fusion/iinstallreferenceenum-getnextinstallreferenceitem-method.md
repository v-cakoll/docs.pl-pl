---
title: "IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum.GetNextInstallReferenceItem
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db7e8bfaf396293f89f4b2e2bb20b5f6f532db19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="d22d0-102">IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="d22d0-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="d22d0-103">Pobiera wskaźnik do następnego [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektów zawartych w tym [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="d22d0-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d22d0-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d22d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d22d0-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="d22d0-106">[out] Zwrócona `IInstallReferenceItem` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d22d0-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d22d0-107">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="d22d0-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d22d0-108">`dwFlags`musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="d22d0-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d22d0-109">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="d22d0-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d22d0-110">`pvReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="d22d0-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d22d0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d22d0-111">Requirements</span></span>  
 <span data-ttu-id="d22d0-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d22d0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d22d0-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d22d0-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d22d0-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d22d0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22d0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d22d0-115">See Also</span></span>  
 [<span data-ttu-id="d22d0-116">IInstallReferenceItem — interfejs</span><span class="sxs-lookup"><span data-stu-id="d22d0-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="d22d0-117">IInstallReferenceEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="d22d0-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
