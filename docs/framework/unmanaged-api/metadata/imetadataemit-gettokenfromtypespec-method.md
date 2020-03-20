---
title: IMetaDataEmit::GetTokenFromTypeSpec — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 8c609d730297881c0ac20dca8569f0e9492638e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175723"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="cc650-102">IMetaDataEmit::GetTokenFromTypeSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc650-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="cc650-103">Pobiera token metadanych dla typu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="cc650-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc650-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc650-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc650-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc650-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="cc650-106">[w] Podpis jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="cc650-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="cc650-107">[w] Liczba bajtów `pvSig`w pliku .</span><span class="sxs-lookup"><span data-stu-id="cc650-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="cc650-108">[na zewnątrz] Token `mdTypeSpec` przypisany.</span><span class="sxs-lookup"><span data-stu-id="cc650-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc650-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc650-109">Requirements</span></span>  
 <span data-ttu-id="cc650-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc650-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc650-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="cc650-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc650-112">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc650-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc650-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc650-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc650-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc650-114">See also</span></span>

- [<span data-ttu-id="cc650-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cc650-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cc650-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc650-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
