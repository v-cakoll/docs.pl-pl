---
title: IMetaDataEmit::SetFieldMarshal — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 1037cd4210605192870d43d88979b89af6536380
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175658"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="2fe70-102">IMetaDataEmit::SetFieldMarshal — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fe70-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="2fe70-103">Ustawia informacje o kierowaniu PInvoke dla pola, zwracania metody lub parametru metody, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="2fe70-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fe70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fe70-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fe70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fe70-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2fe70-106">[w] Token dla elementu danych docelowych.</span><span class="sxs-lookup"><span data-stu-id="2fe70-106">[in] The token for target data item.</span></span> <span data-ttu-id="2fe70-107">Jest to token `mdFieldDef` lub `mdParamDef` token.</span><span class="sxs-lookup"><span data-stu-id="2fe70-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="2fe70-108">[w] Podpis dla typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2fe70-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="2fe70-109">[w] Liczba bajtów `pvNativeType`w pliku .</span><span class="sxs-lookup"><span data-stu-id="2fe70-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fe70-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fe70-110">Requirements</span></span>  
 <span data-ttu-id="2fe70-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fe70-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fe70-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="2fe70-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2fe70-113">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2fe70-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fe70-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fe70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fe70-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fe70-115">See also</span></span>

- [<span data-ttu-id="2fe70-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2fe70-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2fe70-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2fe70-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
