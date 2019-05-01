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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043929"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="b5ce3-102">IMetaDataEmit::DefineProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="b5ce3-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="b5ce3-103">Utworzenie definicji właściwości dla określonego typu z określonego `get` i `set` metod dostępu do metody, a następnie pobiera token do tej definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5ce3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5ce3-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b5ce3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5ce3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b5ce3-106">[in] Token dla klasy lub interfejsu, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="b5ce3-107">[in] Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="b5ce3-108">[in] Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="b5ce3-109">[in] Podpis właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="b5ce3-110">[in] Liczba bajtów w `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="b5ce3-111">[in] Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b5ce3-112">[in] Wartość domyślna dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="b5ce3-113">[in] Liczba (Unicode) znaki w `pValue`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="b5ce3-114">[in] Metoda, która ustawia wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="b5ce3-115">[in] Metoda, która pobiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="b5ce3-116">[in] Tablica innych metod skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="b5ce3-117">Zakończenie tablicy przy użyciu `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="b5ce3-118">[out] `mdProperty` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="b5ce3-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5ce3-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5ce3-119">Requirements</span></span>  
 <span data-ttu-id="b5ce3-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5ce3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5ce3-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b5ce3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5ce3-122">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5ce3-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5ce3-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5ce3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ce3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5ce3-124">See also</span></span>

- [<span data-ttu-id="b5ce3-125">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5ce3-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b5ce3-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5ce3-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
