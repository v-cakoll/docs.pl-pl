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
ms.openlocfilehash: 422ff5d5a2924bf66fee9dad99d57fed9477d0f1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484436"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="26c63-102">IMetaDataImport::GetCustomAttributeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="26c63-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="26c63-103">Pobiera wartość atrybutu niestandardowego, biorąc pod uwagę jego token metadanych.</span><span class="sxs-lookup"><span data-stu-id="26c63-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26c63-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26c63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26c63-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="26c63-106">[in] Token metadanych, który reprezentuje atrybut niestandardowy do pobrania.</span><span class="sxs-lookup"><span data-stu-id="26c63-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="26c63-107">[out, opcjonalny] Token metadanych reprezentujący obiekt, który modyfikuje atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="26c63-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="26c63-108">Ta wartość może być dowolnego typu tokenu metadanych z wyjątkiem `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="26c63-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="26c63-109">[out, opcjonalny] `mdMethodDef` Lub `mdMemberRef` metadanych token reprezentujący <xref:System.Type> zwrócone atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="26c63-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="26c63-110">[out, opcjonalny] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="26c63-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="26c63-111">[out, opcjonalny] Rozmiar w bajtach dane zwrócone w \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="26c63-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26c63-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26c63-112">Remarks</span></span>  
 <span data-ttu-id="26c63-113">Atrybut niestandardowy jest przechowywany jako tablicę danych, formatu, który zrozumieniu przez aparat metadanych.</span><span class="sxs-lookup"><span data-stu-id="26c63-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c63-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26c63-114">Requirements</span></span>  
 <span data-ttu-id="26c63-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26c63-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c63-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="26c63-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26c63-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26c63-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26c63-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c63-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c63-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26c63-119">See also</span></span>
- [<span data-ttu-id="26c63-120">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="26c63-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="26c63-121">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="26c63-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
