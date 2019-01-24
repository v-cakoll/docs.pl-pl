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
ms.openlocfilehash: 4619d5a1444d42c6f3ac43306fbd979a6a70f12b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672178"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="9a7e7-102">IMetaDataImport::GetCustomAttributeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a7e7-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="9a7e7-103">Pobiera wartość atrybutu niestandardowego, biorąc pod uwagę jego token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a7e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a7e7-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a7e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a7e7-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="9a7e7-106">[in] Token metadanych, który reprezentuje atrybut niestandardowy do pobrania.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="9a7e7-107">[out, opcjonalny] Token metadanych reprezentujący obiekt, który modyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="9a7e7-108">Ta wartość może być dowolnego typu tokenu metadanych z wyjątkiem `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="9a7e7-109">[out, opcjonalny] `mdMethodDef` Lub `mdMemberRef` metadanych token reprezentujący <xref:System.Type> zwrócone atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="9a7e7-110">[out, opcjonalny] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="9a7e7-111">[out, opcjonalny] Rozmiar w bajtach dane zwrócone w \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a7e7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a7e7-112">Remarks</span></span>  
 <span data-ttu-id="9a7e7-113">Atrybut niestandardowy jest przechowywany jako tablicę danych, formatu, który zrozumieniu przez aparat metadanych.</span><span class="sxs-lookup"><span data-stu-id="9a7e7-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7e7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a7e7-114">Requirements</span></span>  
 <span data-ttu-id="9a7e7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a7e7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a7e7-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9a7e7-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a7e7-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a7e7-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a7e7-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a7e7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7e7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a7e7-119">See also</span></span>
- [<span data-ttu-id="9a7e7-120">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7e7-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9a7e7-121">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7e7-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
