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
ms.openlocfilehash: 479cb25ad8e1c263d3539a4203ac5bea781eb931
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009382"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="fbc25-102">IMetaDataEmit::DefineProperty — Metoda</span><span class="sxs-lookup"><span data-stu-id="fbc25-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="fbc25-103">Tworzy definicję właściwości określonego typu, z określonymi `get` `set` metodami dostępu, i pobiera token do tej definicji właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbc25-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fbc25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fbc25-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fbc25-106">podczas Token klasy lub interfejsu, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="fbc25-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="fbc25-107">podczas Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="fbc25-108">podczas Flagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="fbc25-109">podczas Podpis właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="fbc25-110">podczas Liczba bajtów w `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="fbc25-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="fbc25-111">podczas Typ wartości domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="fbc25-112">podczas Wartość domyślna właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="fbc25-113">podczas Liczba znaków (Unicode) w `pValue` .</span><span class="sxs-lookup"><span data-stu-id="fbc25-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="fbc25-114">podczas Metoda, która ustawia wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="fbc25-115">podczas Metoda, która pobiera wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="fbc25-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="fbc25-116">podczas Tablica innych metod skojarzonych z właściwością.</span><span class="sxs-lookup"><span data-stu-id="fbc25-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="fbc25-117">Przerwij tablicę przy użyciu `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="fbc25-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="fbc25-118">określoną `mdProperty`Przypisany token.</span><span class="sxs-lookup"><span data-stu-id="fbc25-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbc25-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fbc25-119">Requirements</span></span>  
 <span data-ttu-id="fbc25-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbc25-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbc25-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fbc25-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fbc25-122">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fbc25-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbc25-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbc25-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc25-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbc25-124">See also</span></span>

- [<span data-ttu-id="fbc25-125">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fbc25-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="fbc25-126">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fbc25-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
