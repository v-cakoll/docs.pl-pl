---
title: "IMetaDataImport::GetTypeDefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3e7f2c2fe602ef3464766b62ef12e8f83767bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="52de6-102">IMetaDataImport::GetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="52de6-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="52de6-103">Zwraca informacje o metadanych <xref:System.Type> reprezentowany przez określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="52de6-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52de6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52de6-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="52de6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52de6-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="52de6-106">[in] TypeDef token, który reprezentuje typ do zwracania metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="52de6-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="52de6-107">[out] Bufor zawierający nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="52de6-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="52de6-108">[in] Rozmiar w znaki dwubajtowe `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="52de6-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="52de6-109">[out] Liczba zwracanych w znaki dwubajtowe `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="52de6-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="52de6-110">[out] Wskaźnik do żadnych flag, które modyfikują definicji typu.</span><span class="sxs-lookup"><span data-stu-id="52de6-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="52de6-111">Ta wartość jest maską bitów z [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="52de6-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="52de6-112">[out] Element TypeDef ani TypeRef metadanych token, który reprezentuje typ podstawowy elementu żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="52de6-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52de6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52de6-113">Requirements</span></span>  
 <span data-ttu-id="52de6-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52de6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52de6-115">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52de6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52de6-116">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52de6-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52de6-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52de6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52de6-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52de6-118">See Also</span></span>  
 [<span data-ttu-id="52de6-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="52de6-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="52de6-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="52de6-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
