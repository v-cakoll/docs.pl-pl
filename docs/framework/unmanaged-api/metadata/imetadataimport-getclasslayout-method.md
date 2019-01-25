---
title: IMetaDataImport::GetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52136426be9e8f220d8eb5fc93659f588f007498
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625120"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="3a0a0-102">IMetaDataImport::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a0a0-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="3a0a0-103">Pobiera informacje o układzie dla klasy odwołuje się określony element TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a0a0-104">Syntax</span></span>  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a0a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a0a0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3a0a0-106">[in] Token element TypeDef dla klasy z układem do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="3a0a0-107">[out] Jedna z wartości 1, 2, 4, 8 lub 16, reprezentujący rozmiaru pakietu klasy.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="3a0a0-108">[out] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3a0a0-109">[in] Maksymalny rozmiar `rFieldOffset` tablicy.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="3a0a0-110">[out] Liczba elementów zwróconych w `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="3a0a0-111">[out] Rozmiar w bajtach klasa przedstawiana przez `td`.</span><span class="sxs-lookup"><span data-stu-id="3a0a0-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a0a0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a0a0-112">Requirements</span></span>  
 <span data-ttu-id="3a0a0-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a0a0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a0a0-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3a0a0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a0a0-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a0a0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a0a0-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a0a0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a0a0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a0a0-117">See also</span></span>
- [<span data-ttu-id="3a0a0-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a0a0-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3a0a0-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a0a0-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
