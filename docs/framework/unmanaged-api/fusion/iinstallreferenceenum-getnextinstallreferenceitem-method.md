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
ms.openlocfilehash: ba2abaccfc4a9ae2d1f07677a49a72c980acda24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607504"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="7fb3a-102">IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="7fb3a-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="7fb3a-103">Pobiera wskaźnik do następnego [iinstallreferenceitem —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektów znajdujących się w tym [iinstallreferenceenum —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="7fb3a-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fb3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fb3a-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7fb3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fb3a-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="7fb3a-106">[out] Zwrócony `IInstallReferenceItem` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="7fb3a-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7fb3a-107">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="7fb3a-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="7fb3a-108">`dwFlags` musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="7fb3a-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="7fb3a-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="7fb3a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="7fb3a-110">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7fb3a-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fb3a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fb3a-111">Requirements</span></span>  
 <span data-ttu-id="7fb3a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fb3a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fb3a-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7fb3a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7fb3a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fb3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb3a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fb3a-115">See also</span></span>
- [<span data-ttu-id="7fb3a-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="7fb3a-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="7fb3a-117">IInstallReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="7fb3a-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
