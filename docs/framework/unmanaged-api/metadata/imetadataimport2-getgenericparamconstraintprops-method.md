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
ms.openlocfilehash: 8a1cdff313dae73e3f5e8918ff2ef395c80b115d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490631"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="125cf-102">IMetaDataImport2::GetGenericParamConstraintProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="125cf-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>
<span data-ttu-id="125cf-103">Pobiera metadane skojarzone z ograniczeniem parametru generycznego reprezentowane przez określony token ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="125cf-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="125cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="125cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="125cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="125cf-105">Parameters</span></span>  
 `gpc`  
 <span data-ttu-id="125cf-106">podczas Token do ograniczenia parametru ogólnego, dla którego mają zostać zwrócone metadane.</span><span class="sxs-lookup"><span data-stu-id="125cf-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="125cf-107">określoną Wskaźnik do tokenu, który reprezentuje parametr ogólny, który jest ograniczony.</span><span class="sxs-lookup"><span data-stu-id="125cf-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="125cf-108">określoną Wskaźnik do tokenu TypeDef, TypeRef lub TypeSpec, który reprezentuje ograniczenie `ptGenericParam` .</span><span class="sxs-lookup"><span data-stu-id="125cf-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="125cf-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="125cf-109">Requirements</span></span>  
 <span data-ttu-id="125cf-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="125cf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="125cf-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="125cf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="125cf-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="125cf-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="125cf-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="125cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125cf-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="125cf-114">See also</span></span>

- [<span data-ttu-id="125cf-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="125cf-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="125cf-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="125cf-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
