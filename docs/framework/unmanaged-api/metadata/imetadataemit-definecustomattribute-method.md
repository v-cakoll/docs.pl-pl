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
ms.openlocfilehash: 52190583338f1c1ee9183a98d5f4a6cd7236342d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075687"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="2aeca-102">IMetaDataEmit::DefineCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="2aeca-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="2aeca-103">Tworzy definicję atrybutu niestandardowego za pomocą podpisu określonych metadanych, dołączony do określonego obiektu, a następnie pobiera token do tej definicji atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2aeca-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aeca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2aeca-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2aeca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2aeca-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="2aeca-106">[in] Token elementu właściciela.</span><span class="sxs-lookup"><span data-stu-id="2aeca-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="2aeca-107">[in] Token, który identyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2aeca-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="2aeca-108">[in] Wskaźnik do atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2aeca-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="2aeca-109">[in] Liczba bajtów w `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="2aeca-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="2aeca-110">[out] `mdCustomAttribute` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="2aeca-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2aeca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2aeca-111">Requirements</span></span>  
 <span data-ttu-id="2aeca-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2aeca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2aeca-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2aeca-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2aeca-114">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2aeca-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2aeca-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2aeca-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2aeca-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2aeca-116">See also</span></span>

- [<span data-ttu-id="2aeca-117">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2aeca-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2aeca-118">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2aeca-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
