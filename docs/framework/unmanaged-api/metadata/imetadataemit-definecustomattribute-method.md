---
title: IMetaDataEmit::DefineCustomAttribute — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 9c4ed282e259aa46fc0cb0175214dc51d3d5fbee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175892"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="bb1df-102">IMetaDataEmit::DefineCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb1df-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="bb1df-103">Tworzy definicję atrybutu niestandardowego z określonym podpisem metadanych, który ma być dołączony do określonego obiektu i pobiera token do tej definicji atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="bb1df-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb1df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb1df-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb1df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb1df-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="bb1df-106">[w] Token dla elementu właściciela.</span><span class="sxs-lookup"><span data-stu-id="bb1df-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="bb1df-107">[w] Token, który identyfikuje atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="bb1df-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="bb1df-108">[w] Wskaźnik do atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="bb1df-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="bb1df-109">[w] Liczba bajtów `pCustomAttribute`w pliku .</span><span class="sxs-lookup"><span data-stu-id="bb1df-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="bb1df-110">[na zewnątrz] Token `mdCustomAttribute` przypisany.</span><span class="sxs-lookup"><span data-stu-id="bb1df-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb1df-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb1df-111">Requirements</span></span>  
 <span data-ttu-id="bb1df-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb1df-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb1df-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb1df-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb1df-114">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb1df-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb1df-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb1df-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1df-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb1df-116">See also</span></span>

- [<span data-ttu-id="bb1df-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bb1df-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bb1df-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb1df-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
