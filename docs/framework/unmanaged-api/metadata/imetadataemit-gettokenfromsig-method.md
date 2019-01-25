---
title: IMetaDataEmit::GetTokenFromSig — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 940d913b2b04a510e2ae0e33eaa78b07ba4237c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676799"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="b0bc4-102">IMetaDataEmit::GetTokenFromSig — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0bc4-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="b0bc4-103">Pobiera token dla podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="b0bc4-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0bc4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0bc4-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0bc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0bc4-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="b0bc4-106">[in] Podpis utrwalenia i przechowywane.</span><span class="sxs-lookup"><span data-stu-id="b0bc4-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="b0bc4-107">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="b0bc4-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="b0bc4-108">[out] `mdSignature` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="b0bc4-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0bc4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0bc4-109">Requirements</span></span>  
 <span data-ttu-id="b0bc4-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0bc4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0bc4-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b0bc4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0bc4-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0bc4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0bc4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0bc4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0bc4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0bc4-114">See also</span></span>
- [<span data-ttu-id="b0bc4-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0bc4-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b0bc4-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0bc4-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
