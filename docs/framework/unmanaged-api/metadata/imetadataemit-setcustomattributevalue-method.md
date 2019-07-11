---
title: IMetaDataEmit::SetCustomAttributeValue — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a1f248cf800e9c2bf17d7849e449287cfc493f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737214"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="bf5fa-102">IMetaDataEmit::SetCustomAttributeValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf5fa-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="bf5fa-103">Ustawia lub aktualizuje wartość atrybutu niestandardowego, zdefiniowane przez wcześniejsze wywołanie [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="bf5fa-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf5fa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf5fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf5fa-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="bf5fa-106">[in] Token niestandardowy atrybut docelowy.</span><span class="sxs-lookup"><span data-stu-id="bf5fa-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="bf5fa-107">[in] Wskaźnik do tablicy, która zawiera atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="bf5fa-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="bf5fa-108">[in] Rozmiar w bajtach atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="bf5fa-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5fa-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf5fa-109">Requirements</span></span>  
 <span data-ttu-id="bf5fa-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf5fa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf5fa-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bf5fa-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf5fa-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf5fa-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf5fa-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf5fa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5fa-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf5fa-114">See also</span></span>

- [<span data-ttu-id="bf5fa-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf5fa-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bf5fa-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf5fa-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
