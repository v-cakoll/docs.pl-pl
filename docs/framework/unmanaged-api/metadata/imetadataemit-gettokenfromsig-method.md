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
ms.openlocfilehash: d02943f28435fc00aad8e319aa260a24cca5e307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177589"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="d0156-102">IMetaDataEmit::GetTokenFromSig — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0156-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="d0156-103">Pobiera token dla określonej podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d0156-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0156-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0156-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0156-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0156-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="d0156-106">[w] Podpis, który ma być utrwalony i przechowywany.</span><span class="sxs-lookup"><span data-stu-id="d0156-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d0156-107">[w] Liczba bajtów `pvSig`w pliku .</span><span class="sxs-lookup"><span data-stu-id="d0156-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="d0156-108">[na zewnątrz] Token `mdSignature` przypisany.</span><span class="sxs-lookup"><span data-stu-id="d0156-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0156-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0156-109">Requirements</span></span>  
 <span data-ttu-id="d0156-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0156-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0156-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0156-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0156-112">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0156-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0156-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0156-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0156-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0156-114">See also</span></span>

- [<span data-ttu-id="d0156-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d0156-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d0156-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d0156-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
