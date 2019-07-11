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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85b0edc81a9a861a3eed6a7bc3ffc1ed1db37403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770735"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="d9ebf-102">IMetaDataEmit::GetTokenFromTypeSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9ebf-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="d9ebf-103">Pobiera token metadanych dla typu za pomocą podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ebf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9ebf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9ebf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9ebf-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="d9ebf-106">[in] Podpis jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d9ebf-107">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="d9ebf-108">[out] `mdTypeSpec` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="d9ebf-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ebf-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9ebf-109">Requirements</span></span>  
 <span data-ttu-id="d9ebf-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9ebf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ebf-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d9ebf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9ebf-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9ebf-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9ebf-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9ebf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ebf-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9ebf-114">See also</span></span>

- [<span data-ttu-id="d9ebf-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9ebf-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d9ebf-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9ebf-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
