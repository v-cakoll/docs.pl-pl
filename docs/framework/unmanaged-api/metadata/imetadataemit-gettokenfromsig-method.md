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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139844"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="4c188-102">IMetaDataEmit::GetTokenFromSig — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c188-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="4c188-103">Pobiera token dla podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="4c188-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c188-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c188-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c188-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c188-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="4c188-106">[in] Podpis utrwalenia i przechowywane.</span><span class="sxs-lookup"><span data-stu-id="4c188-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="4c188-107">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="4c188-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="4c188-108">[out] `mdSignature` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="4c188-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c188-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c188-109">Requirements</span></span>  
 <span data-ttu-id="4c188-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c188-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c188-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4c188-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c188-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c188-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c188-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c188-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c188-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c188-114">See also</span></span>

- [<span data-ttu-id="4c188-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c188-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4c188-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c188-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
