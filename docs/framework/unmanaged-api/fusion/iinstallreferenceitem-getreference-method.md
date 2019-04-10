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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213366"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="6605b-102">IInstallReferenceItem::GetReference — Metoda</span><span class="sxs-lookup"><span data-stu-id="6605b-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="6605b-103">Pobiera wskaźnik do [fusion_install_reference —](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktury reprezentowany przez ten [iinstallreferenceitem —](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="6605b-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6605b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6605b-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6605b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6605b-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="6605b-106">[out] Zwrócony `FUSION_INSTALL_REFERENCE` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="6605b-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6605b-107">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="6605b-107">[in] Reserved for future extensibility.</span></span> `dwFlags` <span data-ttu-id="6605b-108">musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="6605b-108">must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6605b-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="6605b-109">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="6605b-110">musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="6605b-110">must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6605b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6605b-111">Requirements</span></span>  
 <span data-ttu-id="6605b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6605b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6605b-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6605b-113">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="6605b-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6605b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6605b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6605b-115">See also</span></span>

- [<span data-ttu-id="6605b-116">IInstallReferenceItem — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6605b-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="6605b-117">FUSION_INSTALL_REFERENCE — Struktura</span><span class="sxs-lookup"><span data-stu-id="6605b-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
