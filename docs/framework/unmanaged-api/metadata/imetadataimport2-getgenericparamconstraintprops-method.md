---
title: IMetaDataImport2::GetGenericParamConstraintProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0503c5bd924793df8143c89e358618fb8844c6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215121"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="44956-102">IMetaDataImport2::GetGenericParamConstraintProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="44956-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="44956-103">Pobiera metadane skojarzone z ograniczenia parametru ogólnego, reprezentowane przez ograniczenie określonego tokenu.</span><span class="sxs-lookup"><span data-stu-id="44956-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44956-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44956-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44956-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44956-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="44956-106">[in] Token do ograniczenia parametru ogólnego, dla której ma zostać zwrócone metadanych.</span><span class="sxs-lookup"><span data-stu-id="44956-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="44956-107">[out] Wskaźnik do tokenu, który reprezentuje parametr generyczny, który jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="44956-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="44956-108">[out] Wskaźnik do elementu TypeDef, TypeRef lub elementu TypeSpec token, który reprezentuje ograniczenie na `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="44956-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44956-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44956-109">Requirements</span></span>  
 <span data-ttu-id="44956-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44956-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44956-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="44956-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44956-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44956-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="44956-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="44956-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="44956-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44956-114">See also</span></span>

- [<span data-ttu-id="44956-115">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="44956-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="44956-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="44956-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
