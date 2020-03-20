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
ms.openlocfilehash: 25b7f478ae0bd05b82fa960561fb8534efe2b4db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175671"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="2ad5c-102">IMetaDataEmit::SetCustomAttributeValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="2ad5c-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="2ad5c-103">Ustawia lub aktualizuje wartość atrybutu niestandardowego zdefiniowanego przez wcześniejsze wywołanie [iMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="2ad5c-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ad5c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ad5c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ad5c-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="2ad5c-106">[w] Token atrybutu niestandardowego docelowego.</span><span class="sxs-lookup"><span data-stu-id="2ad5c-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="2ad5c-107">[w] Wskaźnik do tablicy zawierającej atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="2ad5c-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="2ad5c-108">[w] Rozmiar atrybutu niestandardowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2ad5c-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ad5c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ad5c-109">Requirements</span></span>  
 <span data-ttu-id="2ad5c-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ad5c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ad5c-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ad5c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ad5c-112">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ad5c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ad5c-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ad5c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad5c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ad5c-114">See also</span></span>

- [<span data-ttu-id="2ad5c-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2ad5c-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2ad5c-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ad5c-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
