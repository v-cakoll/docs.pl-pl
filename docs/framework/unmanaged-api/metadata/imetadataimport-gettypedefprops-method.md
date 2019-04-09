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
ms.openlocfilehash: a482c7a06efe888408206f2de569e0a8739b85b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121514"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="7c4b0-102">IMetaDataImport::GetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c4b0-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="7c4b0-103">Zwraca informacje o metadanych <xref:System.Type> reprezentowany przez określony token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c4b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c4b0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7c4b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c4b0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7c4b0-106">[in] TypeDef token, który reprezentuje typ, można zwrócić metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="7c4b0-107">[out] Bufor zawierający nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="7c4b0-108">[in] Rozmiar w znaków `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="7c4b0-109">[out] Liczba znaków dwubajtowych zwracane w `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="7c4b0-110">[out] Wskaźnik do flag, które modyfikują definicji typu.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="7c4b0-111">Ta wartość jest z [cortypeattr —](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="7c4b0-112">[out] Element TypeDef lub TypeRef metadanych token, który reprezentuje typ podstawowy elementu żądanego typu.</span><span class="sxs-lookup"><span data-stu-id="7c4b0-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c4b0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c4b0-113">Requirements</span></span>  
 <span data-ttu-id="7c4b0-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c4b0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c4b0-115">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7c4b0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c4b0-116">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c4b0-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="7c4b0-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7c4b0-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7c4b0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c4b0-118">See also</span></span>

- [<span data-ttu-id="7c4b0-119">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7c4b0-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7c4b0-120">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7c4b0-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
