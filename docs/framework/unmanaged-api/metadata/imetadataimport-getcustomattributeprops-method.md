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
ms.workload: dotnet
ms.openlocfilehash: b1e6ef9443b99b3e6b36154558ce226d421dbc0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="6e307-102">IMetaDataImport::GetCustomAttributeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="6e307-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="6e307-103">Pobiera wartość atrybutu niestandardowego, podane jego token metadanych.</span><span class="sxs-lookup"><span data-stu-id="6e307-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e307-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e307-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e307-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e307-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="6e307-106">[in] Token metadanych, który reprezentuje atrybutu niestandardowego, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="6e307-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="6e307-107">[out, opcjonalnie] Token metadanych reprezentujący obiekt, który modyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6e307-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="6e307-108">Ta wartość może być dowolnego typu token metadanych z wyjątkiem `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="6e307-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="6e307-109">[out, opcjonalnie] `mdMethodDef` Lub `mdMemberRef` metadanych token reprezentujący <xref:System.Type> zwrócony atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6e307-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="6e307-110">[out, opcjonalnie] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="6e307-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="6e307-111">[out, opcjonalnie] Rozmiar w bajtach dane zwrócone w *`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="6e307-111">[out, optional] The size in bytes of the data returned in *`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e307-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e307-112">Remarks</span></span>  
 <span data-ttu-id="6e307-113">Atrybut niestandardowy jest przechowywana jako tablicę danych, formatu, który jest rozpoznawany przez aparat metadanych.</span><span class="sxs-lookup"><span data-stu-id="6e307-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e307-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e307-114">Requirements</span></span>  
 <span data-ttu-id="6e307-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e307-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e307-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e307-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e307-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e307-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e307-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e307-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e307-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e307-119">See Also</span></span>  
 [<span data-ttu-id="6e307-120">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6e307-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6e307-121">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6e307-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
