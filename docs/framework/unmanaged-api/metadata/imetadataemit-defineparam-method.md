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
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431690"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="e585f-102">IMetaDataEmit::DefineParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="e585f-102">IMetaDataEmit::DefineParam Method</span></span>
<span data-ttu-id="e585f-103">Tworzy definicję parametru z określonym podpisem dla metody przywoływanej przez określony token i pobiera token dla tej definicji parametru.</span><span class="sxs-lookup"><span data-stu-id="e585f-103">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e585f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e585f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e585f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e585f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="e585f-106">podczas Token dla metody, której parametr jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="e585f-106">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e585f-107">podczas Numer sekwencyjny parametru.</span><span class="sxs-lookup"><span data-stu-id="e585f-107">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="e585f-108">podczas Nazwa parametru w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="e585f-108">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e585f-109">podczas Flagi dla parametru.</span><span class="sxs-lookup"><span data-stu-id="e585f-109">[in] Flags for the parameter.</span></span> <span data-ttu-id="e585f-110">To jest maska bitów wartości `CorParamAttr`.</span><span class="sxs-lookup"><span data-stu-id="e585f-110">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="e585f-111">[in] `ELEMENT_TYPE_` *\** dla wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="e585f-111">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="e585f-112">podczas Stała wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="e585f-112">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="e585f-113">podczas Rozmiar w znakach Unicode `pValue`.</span><span class="sxs-lookup"><span data-stu-id="e585f-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="e585f-114">określoną Przypisany token `mdParamDef`.</span><span class="sxs-lookup"><span data-stu-id="e585f-114">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e585f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e585f-115">Remarks</span></span>  
 <span data-ttu-id="e585f-116">Wartości sekwencji w `ulParamSeq` zaczynają się od 1 dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="e585f-116">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="e585f-117">Wartość zwracana ma numer sekwencyjny równy 0.</span><span class="sxs-lookup"><span data-stu-id="e585f-117">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e585f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e585f-118">Requirements</span></span>  
 <span data-ttu-id="e585f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e585f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e585f-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e585f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e585f-121">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e585f-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e585f-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e585f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e585f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e585f-123">See also</span></span>

- [<span data-ttu-id="e585f-124">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="e585f-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e585f-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e585f-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
