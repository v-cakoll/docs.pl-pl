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
ms.openlocfilehash: 242618fb2a5ab748132baf68e24240d1ffaf2301
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139844"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="93f82-102">IMetaDataEmit::GetTokenFromSig — Metoda</span><span class="sxs-lookup"><span data-stu-id="93f82-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="93f82-103">Pobiera token dla podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="93f82-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93f82-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93f82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93f82-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="93f82-106">[in] Podpis utrwalenia i przechowywane.</span><span class="sxs-lookup"><span data-stu-id="93f82-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="93f82-107">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="93f82-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="93f82-108">[out] `mdSignature` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="93f82-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f82-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93f82-109">Requirements</span></span>  
 <span data-ttu-id="93f82-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f82-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f82-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="93f82-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93f82-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93f82-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="93f82-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="93f82-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="93f82-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93f82-114">See also</span></span>

- [<span data-ttu-id="93f82-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93f82-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="93f82-116">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93f82-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
