---
title: IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc04bb12e4271a3237ebef140c481620fc01ad7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202381"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="feb98-102">IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="feb98-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="feb98-103">Pobiera wskaźnik do następnego [iinstallreferenceitem —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektów znajdujących się w tym [iinstallreferenceenum —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="feb98-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb98-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="feb98-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feb98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="feb98-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="feb98-106">[out] Zwrócony `IInstallReferenceItem` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="feb98-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="feb98-107">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="feb98-107">[in] Reserved for future extensibility.</span></span> `dwFlags` <span data-ttu-id="feb98-108">musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="feb98-108">must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="feb98-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="feb98-109">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="feb98-110">musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="feb98-110">must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb98-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="feb98-111">Requirements</span></span>  
 <span data-ttu-id="feb98-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feb98-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feb98-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="feb98-113">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="feb98-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="feb98-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="feb98-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="feb98-115">See also</span></span>

- [<span data-ttu-id="feb98-116">IInstallReferenceItem — Interfejs</span><span class="sxs-lookup"><span data-stu-id="feb98-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="feb98-117">IInstallReferenceEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="feb98-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
