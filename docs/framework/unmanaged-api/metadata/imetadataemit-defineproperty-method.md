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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b80833892fc1c0290e94f5de7d9b081529c6a37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085028"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="7649f-102">IMetaDataEmit::DefineProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="7649f-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="7649f-103">Utworzenie definicji właściwości dla określonego typu z określonego `get` i `set` metod dostępu do metody, a następnie pobiera token do tej definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7649f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7649f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7649f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7649f-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7649f-106">[in] Token dla klasy lub interfejsu, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="7649f-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="7649f-107">[in] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="7649f-108">[in] Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="7649f-109">[in] Podpis właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="7649f-110">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="7649f-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="7649f-111">[in] Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="7649f-112">[in] Wartość domyślna dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="7649f-113">[in] Liczba (Unicode) znaki w `pValue`.</span><span class="sxs-lookup"><span data-stu-id="7649f-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="7649f-114">[in] Metoda, która ustawia wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="7649f-115">[in] Metoda, która pobiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="7649f-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="7649f-116">[in] Tablica innych metod skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="7649f-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="7649f-117">Zakończenie tablicy przy użyciu `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="7649f-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="7649f-118">[out] `mdProperty` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="7649f-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7649f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7649f-119">Requirements</span></span>  
 <span data-ttu-id="7649f-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7649f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7649f-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7649f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7649f-122">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7649f-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7649f-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7649f-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7649f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7649f-124">See also</span></span>

- [<span data-ttu-id="7649f-125">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7649f-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7649f-126">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7649f-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
