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
ms.openlocfilehash: be42fea034be4fe5d48874b00db86977a3039a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="42118-102">IMetaDataEmit::GetTokenFromSig — Metoda</span><span class="sxs-lookup"><span data-stu-id="42118-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="42118-103">Pobiera token podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="42118-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42118-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42118-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42118-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42118-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="42118-106">[in] Podpis utrwalenia i przechowywane.</span><span class="sxs-lookup"><span data-stu-id="42118-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="42118-107">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="42118-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="42118-108">[out] `mdSignature` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="42118-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42118-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42118-109">Requirements</span></span>  
 <span data-ttu-id="42118-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42118-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42118-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="42118-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42118-112">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42118-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42118-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42118-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42118-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42118-114">See Also</span></span>  
 [<span data-ttu-id="42118-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="42118-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="42118-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="42118-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
