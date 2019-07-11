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
ms.openlocfilehash: e3868b07ff01f2d1fec79537dd478a2d005f490f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778770"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="f5749-102">IMetaDataImport2::GetGenericParamConstraintProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5749-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="f5749-103">Pobiera metadane skojarzone z ograniczenia parametru ogólnego, reprezentowane przez ograniczenie określonego tokenu.</span><span class="sxs-lookup"><span data-stu-id="f5749-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5749-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5749-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5749-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5749-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="f5749-106">[in] Token do ograniczenia parametru ogólnego, dla której ma zostać zwrócone metadanych.</span><span class="sxs-lookup"><span data-stu-id="f5749-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="f5749-107">[out] Wskaźnik do tokenu, który reprezentuje parametr generyczny, który jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="f5749-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="f5749-108">[out] Wskaźnik do elementu TypeDef, TypeRef lub elementu TypeSpec token, który reprezentuje ograniczenie na `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="f5749-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5749-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5749-109">Requirements</span></span>  
 <span data-ttu-id="f5749-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5749-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5749-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f5749-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5749-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5749-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5749-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5749-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5749-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5749-114">See also</span></span>

- [<span data-ttu-id="f5749-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5749-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="f5749-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5749-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
