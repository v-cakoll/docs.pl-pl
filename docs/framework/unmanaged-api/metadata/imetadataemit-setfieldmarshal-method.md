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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a55a8575a3f8ae04bcc4a148b588cd2361f81cf6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751498"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="65ca2-102">IMetaDataEmit::SetFieldMarshal — Metoda</span><span class="sxs-lookup"><span data-stu-id="65ca2-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="65ca2-103">Ustawia PInvoke organizowanie informacji dla parametru pola, metody zwrotu lub metoda odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="65ca2-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ca2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65ca2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ca2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65ca2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="65ca2-106">[in] Token do docelowego elementu danych.</span><span class="sxs-lookup"><span data-stu-id="65ca2-106">[in] The token for target data item.</span></span> <span data-ttu-id="65ca2-107">Jest to `mdFieldDef` lub `mdParamDef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="65ca2-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="65ca2-108">[in] Podpis dla typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="65ca2-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="65ca2-109">[in] Liczba bajtów w `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="65ca2-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ca2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65ca2-110">Requirements</span></span>  
 <span data-ttu-id="65ca2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ca2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ca2-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="65ca2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65ca2-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65ca2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65ca2-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ca2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ca2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65ca2-115">See also</span></span>

- [<span data-ttu-id="65ca2-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ca2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="65ca2-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="65ca2-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
