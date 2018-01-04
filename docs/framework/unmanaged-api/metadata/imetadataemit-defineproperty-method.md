---
title: "IMetaDataEmit::DefineProperty — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineProperty
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: accc6503cc9fb87d39a429331dc82ff5717f6989
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="24cc7-102">IMetaDataEmit::DefineProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="24cc7-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="24cc7-103">Utworzenie definicji właściwości dla określonego typu z określonym `get` i `set` akcesorów — metoda i pobiera token do tej definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24cc7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24cc7-104">Syntax</span></span>  
  
```  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24cc7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24cc7-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="24cc7-106">[in] Token dla klasy lub interfejsu, na którym jest zdefiniowana właściwość.</span><span class="sxs-lookup"><span data-stu-id="24cc7-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="24cc7-107">[in] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="24cc7-108">[in] Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="24cc7-109">[in] Podpis właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="24cc7-110">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="24cc7-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="24cc7-111">[in] Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="24cc7-112">[in] Wartość domyślna właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="24cc7-113">[in] Liczba (Unicode) znaków `pValue`.</span><span class="sxs-lookup"><span data-stu-id="24cc7-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="24cc7-114">[in] Metoda, która ustawia wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="24cc7-115">[in] Metoda, która pobiera wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="24cc7-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="24cc7-116">[in] Tablica innych metod skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="24cc7-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="24cc7-117">Przerwanie tablicy o `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="24cc7-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="24cc7-118">[out] `mdProperty` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="24cc7-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24cc7-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24cc7-119">Requirements</span></span>  
 <span data-ttu-id="24cc7-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24cc7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24cc7-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="24cc7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24cc7-122">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24cc7-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24cc7-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24cc7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24cc7-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24cc7-124">See Also</span></span>  
 [<span data-ttu-id="24cc7-125">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="24cc7-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="24cc7-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="24cc7-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
