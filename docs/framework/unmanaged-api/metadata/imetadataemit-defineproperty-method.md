---
title: IMetaDataEmit::DefineProperty — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175788"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="dd3bc-102">IMetaDataEmit::DefineProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd3bc-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="dd3bc-103">Tworzy definicję właściwości dla określonego typu, z określonymi `get` i `set` akcesorami metod i pobiera token do tej definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd3bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd3bc-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="dd3bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd3bc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="dd3bc-106">[w] Token dla klasy lub interfejsu, na którym właściwość jest definiowana.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="dd3bc-107">[w] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="dd3bc-108">[w] Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="dd3bc-109">[w] Podpis właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="dd3bc-110">[w] Liczba bajtów `pvSig`w pliku .</span><span class="sxs-lookup"><span data-stu-id="dd3bc-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="dd3bc-111">[w] Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="dd3bc-112">[w] Wartość domyślna właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="dd3bc-113">[w] Liczba znaków (Unicode) `pValue`w pliku .</span><span class="sxs-lookup"><span data-stu-id="dd3bc-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="dd3bc-114">[w] Metoda, która ustawia wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="dd3bc-115">[w] Metoda, która pobiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="dd3bc-116">[w] Tablica innych metod skojarzonych z właściwością.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="dd3bc-117">Zakończ tablicę za `mdTokenNil`pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="dd3bc-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="dd3bc-118">[na zewnątrz] Token `mdProperty` przypisany.</span><span class="sxs-lookup"><span data-stu-id="dd3bc-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd3bc-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd3bc-119">Requirements</span></span>  
 <span data-ttu-id="dd3bc-120">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd3bc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd3bc-121">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="dd3bc-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd3bc-122">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd3bc-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd3bc-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd3bc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3bc-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd3bc-124">See also</span></span>

- [<span data-ttu-id="dd3bc-125">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dd3bc-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dd3bc-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd3bc-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
