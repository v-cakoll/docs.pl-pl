---
title: IInstallReferenceItem::GetReference — Metoda
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd0a554535122b81f5812102c7951f56b294796a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213366"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="a450d-102">IInstallReferenceItem::GetReference — Metoda</span><span class="sxs-lookup"><span data-stu-id="a450d-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="a450d-103">Pobiera wskaźnik do [fusion_install_reference —](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktury reprezentowany przez ten [iinstallreferenceitem —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="a450d-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a450d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a450d-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a450d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a450d-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="a450d-106">[out] Zwrócony `FUSION_INSTALL_REFERENCE` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="a450d-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a450d-107">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="a450d-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a450d-108">`dwFlags` musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="a450d-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a450d-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="a450d-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a450d-110">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="a450d-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a450d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a450d-111">Requirements</span></span>  
 <span data-ttu-id="a450d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a450d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a450d-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a450d-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a450d-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a450d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a450d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a450d-115">See also</span></span>

- [<span data-ttu-id="a450d-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="a450d-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="a450d-117">FUSION_INSTALL_REFERENCE, struktura</span><span class="sxs-lookup"><span data-stu-id="a450d-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
