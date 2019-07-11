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
ms.openlocfilehash: 0dd96b10b5ee2880e0f9ee18048ec8ba2ee0b5ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779061"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="250a8-102">IInstallReferenceEnum::GetNextInstallReferenceItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="250a8-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="250a8-103">Pobiera wskaźnik do następnego [iinstallreferenceitem —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektów znajdujących się w tym [iinstallreferenceenum —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="250a8-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="250a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="250a8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="250a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="250a8-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="250a8-106">[out] Zwrócony `IInstallReferenceItem` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="250a8-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="250a8-107">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="250a8-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="250a8-108">`dwFlags` musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="250a8-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="250a8-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="250a8-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="250a8-110">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="250a8-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="250a8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="250a8-111">Requirements</span></span>  
 <span data-ttu-id="250a8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="250a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="250a8-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="250a8-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="250a8-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="250a8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250a8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="250a8-115">See also</span></span>

- [<span data-ttu-id="250a8-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="250a8-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="250a8-117">IInstallReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="250a8-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
