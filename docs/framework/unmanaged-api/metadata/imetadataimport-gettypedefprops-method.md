---
title: IMetaDataImport::GetTypeDefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12adffbfeb2ce6271774cf44c1a913d7a1414ba4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718614"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="315de-102">IMetaDataImport::GetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="315de-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="315de-103">Zwraca informacje o metadanych <xref:System.Type> reprezentowany przez określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="315de-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="315de-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="315de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="315de-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="315de-106">[in] TypeDef token, który reprezentuje typ, można zwrócić metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="315de-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="315de-107">[out] Bufor zawierający nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="315de-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="315de-108">[in] Rozmiar w znaków `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="315de-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="315de-109">[out] Liczba znaków dwubajtowych zwracane w `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="315de-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="315de-110">[out] Wskaźnik do flag, które modyfikują definicji typu.</span><span class="sxs-lookup"><span data-stu-id="315de-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="315de-111">Ta wartość jest z [cortypeattr —](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="315de-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="315de-112">[out] Element TypeDef lub TypeRef metadanych token, który reprezentuje typ podstawowy elementu żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="315de-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="315de-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="315de-113">Requirements</span></span>  
 <span data-ttu-id="315de-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="315de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="315de-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="315de-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="315de-116">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="315de-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="315de-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="315de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315de-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="315de-118">See also</span></span>
- [<span data-ttu-id="315de-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="315de-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="315de-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="315de-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
