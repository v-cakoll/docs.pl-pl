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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b7cfba90edab44a0053fdfc759417ee7f074401
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132037"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="19abd-102">IMetaDataEmit::SetParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="19abd-102">IMetaDataEmit::SetParamProps Method</span></span>
<span data-ttu-id="19abd-103">Ustawia lub zmienia funkcje parametru metody, która została zdefiniowana przez wcześniejsze wywołanie [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="19abd-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19abd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19abd-104">Syntax</span></span>  
  
```  
HRESULT SetParamProps (   
    [in]  mdParamDef  pd,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19abd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19abd-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="19abd-106">[in] Token do parametru target.</span><span class="sxs-lookup"><span data-stu-id="19abd-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="19abd-107">[in] Nazwa parametru w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="19abd-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="19abd-108">[in] Flagi dla parametru.</span><span class="sxs-lookup"><span data-stu-id="19abd-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="19abd-109">[in] Element ELEMENT_TYPE_ \* wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="19abd-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="19abd-110">[in] Stała wartość dla parametru.</span><span class="sxs-lookup"><span data-stu-id="19abd-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="19abd-111">[in] Rozmiar w znakach (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="19abd-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19abd-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19abd-112">Requirements</span></span>  
 <span data-ttu-id="19abd-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19abd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19abd-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="19abd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19abd-115">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19abd-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19abd-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19abd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19abd-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19abd-117">See also</span></span>

- [<span data-ttu-id="19abd-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="19abd-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="19abd-119">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="19abd-119">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
