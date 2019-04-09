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
ms.openlocfilehash: c27a55166ebc055f324ec45ba6dfd835c8b8bbf6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075746"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="658c1-102">IMetaDataImport::GetCustomAttributeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="658c1-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="658c1-103">Pobiera wartość atrybutu niestandardowego, biorąc pod uwagę jego token metadanych.</span><span class="sxs-lookup"><span data-stu-id="658c1-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="658c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="658c1-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="658c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="658c1-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="658c1-106">[in] Token metadanych, który reprezentuje atrybut niestandardowy do pobrania.</span><span class="sxs-lookup"><span data-stu-id="658c1-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="658c1-107">[out, opcjonalny] Token metadanych reprezentujący obiekt, który modyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="658c1-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="658c1-108">Ta wartość może być dowolnego typu tokenu metadanych z wyjątkiem `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="658c1-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="658c1-109">[out, opcjonalny] `mdMethodDef` Lub `mdMemberRef` metadanych token reprezentujący <xref:System.Type> zwrócone atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="658c1-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="658c1-110">[out, opcjonalny] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="658c1-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="658c1-111">[out, opcjonalny] Rozmiar w bajtach dane zwrócone w \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="658c1-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="658c1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="658c1-112">Remarks</span></span>  
 <span data-ttu-id="658c1-113">Atrybut niestandardowy jest przechowywany jako tablicę danych, formatu, który zrozumieniu przez aparat metadanych.</span><span class="sxs-lookup"><span data-stu-id="658c1-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="658c1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="658c1-114">Requirements</span></span>  
 <span data-ttu-id="658c1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="658c1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="658c1-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="658c1-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="658c1-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="658c1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="658c1-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="658c1-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="658c1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="658c1-119">See also</span></span>

- [<span data-ttu-id="658c1-120">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="658c1-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="658c1-121">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="658c1-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
