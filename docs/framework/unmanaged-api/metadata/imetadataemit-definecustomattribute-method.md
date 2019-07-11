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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 994e007eabf8b7fdcf5446d905c06eb4ab91bb3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777675"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="56314-102">IMetaDataEmit::DefineCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="56314-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="56314-103">Tworzy definicję atrybutu niestandardowego za pomocą podpisu określonych metadanych, dołączony do określonego obiektu, a następnie pobiera token do tej definicji atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="56314-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56314-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56314-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56314-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56314-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="56314-106">[in] Token elementu właściciela.</span><span class="sxs-lookup"><span data-stu-id="56314-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="56314-107">[in] Token, który identyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="56314-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="56314-108">[in] Wskaźnik do atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="56314-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="56314-109">[in] Liczba bajtów w `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="56314-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="56314-110">[out] `mdCustomAttribute` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="56314-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56314-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56314-111">Requirements</span></span>  
 <span data-ttu-id="56314-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56314-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56314-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="56314-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56314-114">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56314-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56314-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56314-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56314-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56314-116">See also</span></span>

- [<span data-ttu-id="56314-117">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="56314-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="56314-118">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="56314-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
