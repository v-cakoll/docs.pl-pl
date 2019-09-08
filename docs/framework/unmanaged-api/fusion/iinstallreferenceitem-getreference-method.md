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
ms.openlocfilehash: 9395fcc6d896114c25770edbc17761323285099f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796393"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="6f4b9-102">IInstallReferenceItem::GetReference — Metoda</span><span class="sxs-lookup"><span data-stu-id="6f4b9-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="6f4b9-103">Pobiera wskaźnik do struktury [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) reprezentowanej przez ten obiekt [IInstallReferenceItem](iinstallreferenceitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6f4b9-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f4b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f4b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f4b9-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="6f4b9-106">określoną Zwrócony `FUSION_INSTALL_REFERENCE` wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="6f4b9-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6f4b9-107">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6f4b9-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="6f4b9-108">`dwFlags`musi mieć wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="6f4b9-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6f4b9-109">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6f4b9-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="6f4b9-110">`pvReserved`musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="6f4b9-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f4b9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f4b9-111">Requirements</span></span>  
 <span data-ttu-id="6f4b9-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f4b9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f4b9-113">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6f4b9-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6f4b9-114">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f4b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4b9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f4b9-115">See also</span></span>

- [<span data-ttu-id="6f4b9-116">IInstallReferenceItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f4b9-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="6f4b9-117">FUSION_INSTALL_REFERENCE, struktura</span><span class="sxs-lookup"><span data-stu-id="6f4b9-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
