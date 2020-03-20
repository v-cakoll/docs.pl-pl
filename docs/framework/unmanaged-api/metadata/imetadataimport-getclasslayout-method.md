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
ms.openlocfilehash: e02d7dd4b287d027b633ae9bf2e98e036062bdd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175411"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="8ad20-102">IMetaDataImport::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ad20-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="8ad20-103">Pobiera informacje o układzie dla klasy, do którego odwołuje się określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="8ad20-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ad20-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ad20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ad20-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8ad20-106">[w] TypeDef token dla klasy z układu do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="8ad20-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="8ad20-107">[na zewnątrz] Jedna z wartości 1, 2, 4, 8 lub 16, reprezentująca rozmiar opakowania klasy.</span><span class="sxs-lookup"><span data-stu-id="8ad20-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="8ad20-108">[na zewnątrz] Tablica [wartości COR_FIELD_OFFSET.](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)</span><span class="sxs-lookup"><span data-stu-id="8ad20-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8ad20-109">[w] Maksymalny rozmiar `rFieldOffset` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8ad20-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="8ad20-110">[na zewnątrz] Liczba elementów zwróconych w `rFieldOffset`programie .</span><span class="sxs-lookup"><span data-stu-id="8ad20-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="8ad20-111">[na zewnątrz] Rozmiar w bajtach klasy reprezentowanej przez `td`.</span><span class="sxs-lookup"><span data-stu-id="8ad20-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad20-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ad20-112">Requirements</span></span>  
 <span data-ttu-id="8ad20-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad20-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad20-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ad20-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ad20-115">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ad20-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ad20-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad20-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad20-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ad20-117">See also</span></span>

- [<span data-ttu-id="8ad20-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8ad20-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8ad20-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ad20-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
