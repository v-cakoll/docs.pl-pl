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
ms.openlocfilehash: 13220dcfdd260688494d5aebc50f94abf8a82215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177504"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="9cebe-102">IMetaDataEmit::SetParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cebe-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="9cebe-103">Ustawia lub zmienia funkcje parametru metody zdefiniowanego przez wcześniejsze wywołanie [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="9cebe-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cebe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cebe-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9cebe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cebe-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="9cebe-106">[w] Token parametru docelowego.</span><span class="sxs-lookup"><span data-stu-id="9cebe-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="9cebe-107">[w] Nazwa parametru w Unicode.</span><span class="sxs-lookup"><span data-stu-id="9cebe-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="9cebe-108">[w] Flagi parametru.</span><span class="sxs-lookup"><span data-stu-id="9cebe-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="9cebe-109">[w] Wartość ELEMENT_TYPE_\* dla wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="9cebe-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9cebe-110">[w] Stała wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="9cebe-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="9cebe-111">[w] Rozmiar w znakach (Unicode) . `pValue`</span><span class="sxs-lookup"><span data-stu-id="9cebe-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cebe-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cebe-112">Requirements</span></span>  
 <span data-ttu-id="9cebe-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cebe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cebe-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="9cebe-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9cebe-115">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9cebe-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cebe-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cebe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cebe-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cebe-117">See also</span></span>

- [<span data-ttu-id="9cebe-118">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9cebe-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9cebe-119">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9cebe-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
