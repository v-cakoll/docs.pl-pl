---
title: IMetaDataEmit::DefineField — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177712"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="8b636-102">IMetaDataEmit::DefineField — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b636-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="8b636-103">Tworzy definicję dla pola z określonym podpisem metadanych i pobiera token do tej definicji pola.</span><span class="sxs-lookup"><span data-stu-id="8b636-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b636-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b636-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (
    [in]  mdTypeDef   td,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwFieldFlags,
    [in]  PCCOR_SIGNATURE pvSigBlob,
    [in]  ULONG       cbSigBlob,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue,
    [out] mdFieldDef  *pmd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b636-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b636-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8b636-106">[w] Token `mdTypeDef` dla otaczającej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8b636-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="8b636-107">[w] Nazwa pola w unicode.</span><span class="sxs-lookup"><span data-stu-id="8b636-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="8b636-108">[w] Atrybuty pola.</span><span class="sxs-lookup"><span data-stu-id="8b636-108">[in] The field attributes.</span></span> <span data-ttu-id="8b636-109">Jest to maska `CorFieldAttr` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="8b636-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8b636-110">[w] Podpis pola jako obiekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="8b636-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8b636-111">[w] Liczba bajtów `pvSigBlob`w pliku .</span><span class="sxs-lookup"><span data-stu-id="8b636-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="8b636-112">[w] Dla `ELEMENT_TYPE_` *\** wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="8b636-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="8b636-113">Jest to `CorElementType` wartość.</span><span class="sxs-lookup"><span data-stu-id="8b636-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="8b636-114">Jeśli nie zdefiniowano stałej wartości `ELEMENT_TYPE_END`dla pola, należy użyć programu .</span><span class="sxs-lookup"><span data-stu-id="8b636-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8b636-115">[w] Stała wartość pola.</span><span class="sxs-lookup"><span data-stu-id="8b636-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="8b636-116">[w] Rozmiar w znakach (Unicode) . `pValue`</span><span class="sxs-lookup"><span data-stu-id="8b636-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="8b636-117">[na zewnątrz] Token `mdFieldDef` przypisany.</span><span class="sxs-lookup"><span data-stu-id="8b636-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b636-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b636-118">Requirements</span></span>  
 <span data-ttu-id="8b636-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b636-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b636-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="8b636-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b636-121">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b636-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b636-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b636-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b636-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b636-123">See also</span></span>

- [<span data-ttu-id="8b636-124">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8b636-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8b636-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b636-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
