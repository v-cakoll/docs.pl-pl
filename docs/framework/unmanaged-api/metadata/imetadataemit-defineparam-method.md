---
title: IMetaDataEmit::DefineParam — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 86711d107636505ab7aa23f0f72f70bd3e27635d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167775"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="b74fc-102">IMetaDataEmit::DefineParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="b74fc-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="b74fc-103">Tworzy definicję parametrów o określonej sygnaturze metody odwołuje się określony token, a następnie pobiera token dla tej definicji parametru.</span><span class="sxs-lookup"><span data-stu-id="b74fc-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b74fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b74fc-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b74fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b74fc-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b74fc-106">[in] Token dla metody, w której parametr jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="b74fc-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="b74fc-107">[in] Numer sekwencji parametru.</span><span class="sxs-lookup"><span data-stu-id="b74fc-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="b74fc-108">[in] Nazwa parametru w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="b74fc-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="b74fc-109">[in] Flagi unikatowe dla parametru.</span><span class="sxs-lookup"><span data-stu-id="b74fc-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="b74fc-110">Jest to z `CorParamAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="b74fc-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="b74fc-111">[in] `ELEMENT_TYPE_` *\** wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="b74fc-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b74fc-112">[in] Stała wartość dla parametru.</span><span class="sxs-lookup"><span data-stu-id="b74fc-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="b74fc-113">[in] Rozmiar w znaki Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="b74fc-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="b74fc-114">[out] `mdParamDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="b74fc-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b74fc-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b74fc-115">Remarks</span></span>  
 <span data-ttu-id="b74fc-116">Sekwencja wartości w `ulParamSeq` zaczynają się od 1 dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="b74fc-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="b74fc-117">Wartość zwracana ma kolejny numer 0.</span><span class="sxs-lookup"><span data-stu-id="b74fc-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b74fc-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b74fc-118">Requirements</span></span>  
 <span data-ttu-id="b74fc-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b74fc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b74fc-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b74fc-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b74fc-121">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b74fc-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b74fc-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b74fc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74fc-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b74fc-123">See also</span></span>

- [<span data-ttu-id="b74fc-124">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b74fc-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b74fc-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b74fc-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
