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
ms.openlocfilehash: 9d64a1ef21cd4fa4224609c7cd415c1611313769
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777547"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="21f74-102">IMetaDataEmit::DefineParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="21f74-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="21f74-103">Tworzy definicję parametrów o określonej sygnaturze metody odwołuje się określony token, a następnie pobiera token dla tej definicji parametru.</span><span class="sxs-lookup"><span data-stu-id="21f74-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21f74-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="21f74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21f74-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="21f74-106">[in] Token dla metody, w której parametr jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="21f74-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="21f74-107">[in] Numer sekwencji parametru.</span><span class="sxs-lookup"><span data-stu-id="21f74-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="21f74-108">[in] Nazwa parametru w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="21f74-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="21f74-109">[in] Flagi unikatowe dla parametru.</span><span class="sxs-lookup"><span data-stu-id="21f74-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="21f74-110">Jest to z `CorParamAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="21f74-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="21f74-111">[in] `ELEMENT_TYPE_` *\** wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="21f74-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="21f74-112">[in] Stała wartość dla parametru.</span><span class="sxs-lookup"><span data-stu-id="21f74-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="21f74-113">[in] Rozmiar w znaki Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="21f74-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="21f74-114">[out] `mdParamDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="21f74-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21f74-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21f74-115">Remarks</span></span>  
 <span data-ttu-id="21f74-116">Sekwencja wartości w `ulParamSeq` zaczynają się od 1 dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="21f74-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="21f74-117">Wartość zwracana ma kolejny numer 0.</span><span class="sxs-lookup"><span data-stu-id="21f74-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f74-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21f74-118">Requirements</span></span>  
 <span data-ttu-id="21f74-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f74-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f74-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="21f74-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21f74-121">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21f74-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21f74-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f74-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f74-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21f74-123">See also</span></span>

- [<span data-ttu-id="21f74-124">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="21f74-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="21f74-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="21f74-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
