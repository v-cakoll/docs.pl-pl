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
ms.openlocfilehash: 09256deafdb42847f369664ec8c4bc96d72424d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177609"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="7f868-102">IMetaDataEmit::GetTokenFromTypeSpec — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f868-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="7f868-103">Pobiera token metadanych dla typu za pomocą podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="7f868-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f868-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f868-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f868-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f868-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="7f868-106">[in] Podpis jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="7f868-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="7f868-107">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="7f868-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="7f868-108">[out] `mdTypeSpec` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="7f868-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f868-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f868-109">Requirements</span></span>  
 <span data-ttu-id="7f868-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f868-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f868-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7f868-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f868-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f868-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7f868-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7f868-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f868-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f868-114">See also</span></span>

- [<span data-ttu-id="7f868-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7f868-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7f868-116">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7f868-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
