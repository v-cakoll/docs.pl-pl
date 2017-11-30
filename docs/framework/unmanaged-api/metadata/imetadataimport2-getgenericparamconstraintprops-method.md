---
title: "IMetaDataImport2::GetGenericParamConstraintProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetGenericParamConstraintProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7d1e560dd511758652e1acbc262b4ddc3efdd12c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="2bbbb-102">IMetaDataImport2::GetGenericParamConstraintProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="2bbbb-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="2bbbb-103">Pobiera metadane skojarzone z ograniczenia parametru ogólnego reprezentowany przez ograniczenie określony token.</span><span class="sxs-lookup"><span data-stu-id="2bbbb-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bbbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2bbbb-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bbbb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bbbb-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="2bbbb-106">[in] Token do ograniczenia parametru ogólnego, dla którego ma zostać zwrócona metadanych.</span><span class="sxs-lookup"><span data-stu-id="2bbbb-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="2bbbb-107">[out] Wskaźnik do tokenu, który reprezentuje parametr generyczny, który jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="2bbbb-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="2bbbb-108">[out] Wskaźnik do elementu TypeDef, TypeRef lub elementu TypeSpec token, który reprezentuje ograniczenie na `ptGenericParam`.</span><span class="sxs-lookup"><span data-stu-id="2bbbb-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bbbb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2bbbb-109">Requirements</span></span>  
 <span data-ttu-id="2bbbb-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bbbb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bbbb-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2bbbb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2bbbb-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bbbb-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2bbbb-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbbb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbbb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bbbb-114">See Also</span></span>  
 [<span data-ttu-id="2bbbb-115">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="2bbbb-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="2bbbb-116">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="2bbbb-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
