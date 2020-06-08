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
ms.openlocfilehash: 320cfae93f8aae94f9315e8e20ed6cf7f9cced7c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491319"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="03e95-102">IMetaDataImport::GetCustomAttributeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="03e95-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="03e95-103">Pobiera wartość atrybutu niestandardowego z uwzględnieniem jego tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="03e95-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03e95-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03e95-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03e95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03e95-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="03e95-106">podczas Token metadanych, który reprezentuje atrybut niestandardowy do pobrania.</span><span class="sxs-lookup"><span data-stu-id="03e95-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="03e95-107">[out, opcjonalne] Token metadanych reprezentujący obiekt, który modyfikuje atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="03e95-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="03e95-108">Ta wartość może być dowolnego typu tokenu metadanych z wyjątkiem `mdCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="03e95-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="03e95-109">[out, opcjonalne] `mdMethodDef` `mdMemberRef` Token metadanych lub reprezentujący <xref:System.Type> zwrócony atrybut niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="03e95-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="03e95-110">[out, opcjonalne] Wskaźnik do tablicy danych, która jest wartością atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="03e95-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="03e95-111">[out, opcjonalne] Rozmiar w bajtach danych zwróconych w \* `ppBlob` .</span><span class="sxs-lookup"><span data-stu-id="03e95-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03e95-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03e95-112">Remarks</span></span>  
 <span data-ttu-id="03e95-113">Atrybut niestandardowy jest przechowywany jako tablica danych, format zrozumiały dla aparatu metadanych.</span><span class="sxs-lookup"><span data-stu-id="03e95-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03e95-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03e95-114">Requirements</span></span>  
 <span data-ttu-id="03e95-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03e95-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03e95-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="03e95-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03e95-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03e95-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03e95-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03e95-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e95-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03e95-119">See also</span></span>

- [<span data-ttu-id="03e95-120">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03e95-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="03e95-121">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="03e95-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
