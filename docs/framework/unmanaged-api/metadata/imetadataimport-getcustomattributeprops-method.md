---
title: IMetaDataImport::GetCustomAttributeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c714915651d8660a739d8ee6518fc3814af4c08d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782415"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="77d54-102">IMetaDataImport::GetCustomAttributeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="77d54-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="77d54-103">Pobiera wartość atrybutu niestandardowego, biorąc pod uwagę jego token metadanych.</span><span class="sxs-lookup"><span data-stu-id="77d54-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77d54-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77d54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77d54-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="77d54-106">[in] Token metadanych, który reprezentuje atrybut niestandardowy do pobrania.</span><span class="sxs-lookup"><span data-stu-id="77d54-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="77d54-107">[out, opcjonalny] Token metadanych reprezentujący obiekt, który modyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="77d54-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="77d54-108">Ta wartość może być dowolnego typu tokenu metadanych z wyjątkiem `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="77d54-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="77d54-109">[out, opcjonalny] `mdMethodDef` Lub `mdMemberRef` metadanych token reprezentujący <xref:System.Type> zwrócone atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="77d54-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="77d54-110">[out, opcjonalny] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="77d54-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="77d54-111">[out, opcjonalny] Rozmiar w bajtach dane zwrócone w \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="77d54-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d54-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77d54-112">Remarks</span></span>  
 <span data-ttu-id="77d54-113">Atrybut niestandardowy jest przechowywany jako tablicę danych, formatu, który zrozumieniu przez aparat metadanych.</span><span class="sxs-lookup"><span data-stu-id="77d54-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d54-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77d54-114">Requirements</span></span>  
 <span data-ttu-id="77d54-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77d54-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d54-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="77d54-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77d54-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77d54-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77d54-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d54-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d54-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77d54-119">See also</span></span>

- [<span data-ttu-id="77d54-120">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="77d54-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="77d54-121">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="77d54-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
