---
title: "IMetaDataImport::GetCustomAttributeProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 415b1dc67bd3ae3638edd61558cc9e13ebf03fd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="6a801-102">IMetaDataImport::GetCustomAttributeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a801-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="6a801-103">Pobiera wartość atrybutu niestandardowego, podane jego token metadanych.</span><span class="sxs-lookup"><span data-stu-id="6a801-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a801-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a801-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a801-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a801-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="6a801-106">[in] Token metadanych, który reprezentuje atrybutu niestandardowego, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="6a801-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="6a801-107">[out, opcjonalnie] Token metadanych reprezentujący obiekt, który modyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6a801-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="6a801-108">Ta wartość może być dowolnego typu token metadanych z wyjątkiem `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="6a801-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="6a801-109">[out, opcjonalnie] `mdMethodDef` Lub `mdMemberRef` metadanych token reprezentujący <xref:System.Type> zwrócony atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6a801-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="6a801-110">[out, opcjonalnie] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6a801-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="6a801-111">[out, opcjonalnie] Rozmiar w bajtach dane zwrócone w *`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="6a801-111">[out, optional] The size in bytes of the data returned in *`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a801-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a801-112">Remarks</span></span>  
 <span data-ttu-id="6a801-113">Atrybut niestandardowy jest przechowywana jako tablicę danych, formatu, który jest rozpoznawany przez aparat metadanych.</span><span class="sxs-lookup"><span data-stu-id="6a801-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a801-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a801-114">Requirements</span></span>  
 <span data-ttu-id="6a801-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a801-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a801-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a801-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a801-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a801-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a801-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a801-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a801-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a801-119">See Also</span></span>  
 [<span data-ttu-id="6a801-120">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="6a801-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6a801-121">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="6a801-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
