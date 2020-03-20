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
ms.openlocfilehash: 2807458549db02598ba05f2aa80fa6ea6fbc5a13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177690"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="c83f7-102">IMetaDataEmit::DefineParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="c83f7-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="c83f7-103">Tworzy definicję parametru z określonym podpisem dla metody, do którego odwołuje się określony token i pobiera token dla tej definicji parametru.</span><span class="sxs-lookup"><span data-stu-id="c83f7-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c83f7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c83f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c83f7-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="c83f7-106">[w] Token dla metody, której parametr jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="c83f7-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="c83f7-107">[w] Numer sekwencyjny parametru.</span><span class="sxs-lookup"><span data-stu-id="c83f7-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="c83f7-108">[w] Nazwa parametru w Unicode.</span><span class="sxs-lookup"><span data-stu-id="c83f7-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="c83f7-109">[w] Flagi dla parametru.</span><span class="sxs-lookup"><span data-stu-id="c83f7-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="c83f7-110">Jest to maska `CorParamAttr` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="c83f7-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="c83f7-111">[w] `ELEMENT_TYPE_` dla wartości stałej. *\**</span><span class="sxs-lookup"><span data-stu-id="c83f7-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c83f7-112">[w] Stała wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="c83f7-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="c83f7-113">[w] Rozmiar w znakach Unicode `pValue`.</span><span class="sxs-lookup"><span data-stu-id="c83f7-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="c83f7-114">[na zewnątrz] Token `mdParamDef` przypisany.</span><span class="sxs-lookup"><span data-stu-id="c83f7-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c83f7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c83f7-115">Remarks</span></span>  
 <span data-ttu-id="c83f7-116">Wartości sekwencji `ulParamSeq` na początku od 1 dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="c83f7-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="c83f7-117">Zwracana wartość ma numer sekwencyjny 0.</span><span class="sxs-lookup"><span data-stu-id="c83f7-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c83f7-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c83f7-118">Requirements</span></span>  
 <span data-ttu-id="c83f7-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c83f7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c83f7-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="c83f7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c83f7-121">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c83f7-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c83f7-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c83f7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83f7-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c83f7-123">See also</span></span>

- [<span data-ttu-id="c83f7-124">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c83f7-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c83f7-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c83f7-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
