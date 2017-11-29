---
title: "IMetaDataEmit::DefineParam — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5abe9cf0385a42645468bf58c2f81223ac4eeead
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="e869e-102">IMetaDataEmit::DefineParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="e869e-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="e869e-103">Tworzy definicję parametru z określoną sygnaturą dla metody odwołuje się określony token i pobiera token dla tej definicji parametru.</span><span class="sxs-lookup"><span data-stu-id="e869e-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e869e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e869e-104">Syntax</span></span>  
  
```  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e869e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e869e-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="e869e-106">[in] Token metody zdefiniowano którego parametr.</span><span class="sxs-lookup"><span data-stu-id="e869e-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e869e-107">[in] Numer sekwencji parametru.</span><span class="sxs-lookup"><span data-stu-id="e869e-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="e869e-108">[in] Nazwa parametru w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="e869e-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e869e-109">[in] Flagi dla parametru.</span><span class="sxs-lookup"><span data-stu-id="e869e-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="e869e-110">To jest maską bitów z `CorParamAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="e869e-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e869e-111">[in] `ELEMENT_TYPE_`  *\**  wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="e869e-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e869e-112">[in] Wartość stała dla parametru.</span><span class="sxs-lookup"><span data-stu-id="e869e-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e869e-113">[in] Rozmiar w znaki Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="e869e-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="e869e-114">[out] `mdParamDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="e869e-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e869e-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e869e-115">Remarks</span></span>  
 <span data-ttu-id="e869e-116">Sekwencja wartości w `ulParamSeq` zaczynać się od 1 do parametrów.</span><span class="sxs-lookup"><span data-stu-id="e869e-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="e869e-117">Wartość zwrotna ma numer sekwencji 0.</span><span class="sxs-lookup"><span data-stu-id="e869e-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e869e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e869e-118">Requirements</span></span>  
 <span data-ttu-id="e869e-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e869e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e869e-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e869e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e869e-121">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e869e-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e869e-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e869e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e869e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e869e-123">See Also</span></span>  
 [<span data-ttu-id="e869e-124">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="e869e-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="e869e-125">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="e869e-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
