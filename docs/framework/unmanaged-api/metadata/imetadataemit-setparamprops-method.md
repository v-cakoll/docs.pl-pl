---
title: IMetaDataEmit::SetParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: 813460aa027b259866b168d426fd28502b5c4465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432497"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="4ae9b-102">IMetaDataEmit::SetParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="4ae9b-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="4ae9b-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="4ae9b-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ae9b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ae9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ae9b-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="4ae9b-106">[in] The token for the target parameter.</span><span class="sxs-lookup"><span data-stu-id="4ae9b-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="4ae9b-107">[in] The name of the parameter in Unicode.</span><span class="sxs-lookup"><span data-stu-id="4ae9b-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="4ae9b-108">[in] The flags for the parameter.</span><span class="sxs-lookup"><span data-stu-id="4ae9b-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="4ae9b-109">[in] The ELEMENT_TYPE_\* for the constant value.</span><span class="sxs-lookup"><span data-stu-id="4ae9b-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="4ae9b-110">[in] The constant value for the parameter.</span><span class="sxs-lookup"><span data-stu-id="4ae9b-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="4ae9b-111">[in] The size in (Unicode) characters of `pValue`.</span><span class="sxs-lookup"><span data-stu-id="4ae9b-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ae9b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ae9b-112">Requirements</span></span>  
 <span data-ttu-id="4ae9b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ae9b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ae9b-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ae9b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ae9b-115">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4ae9b-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ae9b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ae9b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae9b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ae9b-117">See also</span></span>

- [<span data-ttu-id="4ae9b-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ae9b-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4ae9b-119">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4ae9b-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
