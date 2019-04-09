---
title: IMetaDataImport2::GetGenericParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55a765fe3942cbf71a8460187e829dc7f3ca877e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082338"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="2212b-102">IMetaDataImport2::GetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="2212b-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="2212b-103">Pobiera metadane skojarzone z parametru ogólnego, reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="2212b-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2212b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2212b-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2212b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2212b-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="2212b-106">[in] Token, który reprezentuje parametr ogólny, dla której ma zostać zwrócone metadanych.</span><span class="sxs-lookup"><span data-stu-id="2212b-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="2212b-107">[out] Numer porządkowy położenie `Type` parametr w Konstruktorze nadrzędnej lub metody.</span><span class="sxs-lookup"><span data-stu-id="2212b-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="2212b-108">[out] Wartość [corgenericparamattr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące `Type` dla parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="2212b-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="2212b-109">[out] Element TypeDef lub MethodDef token reprezentujący właściciela parametru.</span><span class="sxs-lookup"><span data-stu-id="2212b-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="2212b-110">[out] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2212b-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="2212b-111">[out] Nazwa parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="2212b-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2212b-112">[in] Rozmiar `wzName` buforu.</span><span class="sxs-lookup"><span data-stu-id="2212b-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2212b-113">[out] Rozmiar zwróconego nazwę w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="2212b-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2212b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2212b-114">Requirements</span></span>  
 <span data-ttu-id="2212b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2212b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2212b-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2212b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2212b-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2212b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="2212b-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2212b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2212b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2212b-119">See also</span></span>

- [<span data-ttu-id="2212b-120">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2212b-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="2212b-121">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2212b-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
