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
ms.openlocfilehash: b9ded6b4e0ac8f3e70fd0145ab6e2410c3b38e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448677"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="099ae-102">IMetaDataImport2::GetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="099ae-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="099ae-103">Pobiera metadane skojarzone z parametru ogólnego reprezentowany przez określony token.</span><span class="sxs-lookup"><span data-stu-id="099ae-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="099ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="099ae-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="099ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="099ae-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="099ae-106">[in] Token, który reprezentuje parametr generyczny, dla którego ma zostać zwrócona metadanych.</span><span class="sxs-lookup"><span data-stu-id="099ae-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="099ae-107">[out] {Numer porządkowy pozycja `Type` parametru w nadrzędnej konstruktora lub metody.</span><span class="sxs-lookup"><span data-stu-id="099ae-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="099ae-108">[out] Wartość [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące `Type` dla parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="099ae-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="099ae-109">[out] Token TypeDef lub MethodDef, który reprezentuje właściciela parametru.</span><span class="sxs-lookup"><span data-stu-id="099ae-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="099ae-110">[out] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="099ae-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="099ae-111">[out] Nazwa parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="099ae-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="099ae-112">[in] Rozmiar `wzName` buforu.</span><span class="sxs-lookup"><span data-stu-id="099ae-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="099ae-113">[out] Zwrócony rozmiar nazwy, w znaki dwubajtowe.</span><span class="sxs-lookup"><span data-stu-id="099ae-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="099ae-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="099ae-114">Requirements</span></span>  
 <span data-ttu-id="099ae-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="099ae-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="099ae-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="099ae-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="099ae-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="099ae-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="099ae-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="099ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099ae-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="099ae-119">See Also</span></span>  
 [<span data-ttu-id="099ae-120">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="099ae-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="099ae-121">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="099ae-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
