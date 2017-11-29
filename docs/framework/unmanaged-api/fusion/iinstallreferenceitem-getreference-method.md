---
title: "IInstallReferenceItem::GetReference — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceItem.GetReference
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8686e27e63d7363e61bf4c8f1898b71d21fda52b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="4bfa7-102">IInstallReferenceItem::GetReference — Metoda</span><span class="sxs-lookup"><span data-stu-id="4bfa7-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="4bfa7-103">Pobiera wskaźnik do [fusion_install_reference —](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) reprezentowany przez to struktura [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="4bfa7-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bfa7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bfa7-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bfa7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bfa7-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="4bfa7-106">[out] Zwrócona `FUSION_INSTALL_REFERENCE` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="4bfa7-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4bfa7-107">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="4bfa7-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4bfa7-108">`dwFlags`musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="4bfa7-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4bfa7-109">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="4bfa7-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4bfa7-110">`pvReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="4bfa7-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bfa7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bfa7-111">Requirements</span></span>  
 <span data-ttu-id="4bfa7-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bfa7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bfa7-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4bfa7-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4bfa7-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bfa7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bfa7-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4bfa7-115">See Also</span></span>  
 [<span data-ttu-id="4bfa7-116">IInstallReferenceItem — interfejs</span><span class="sxs-lookup"><span data-stu-id="4bfa7-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="4bfa7-117">Fusion_install_reference — struktura</span><span class="sxs-lookup"><span data-stu-id="4bfa7-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
