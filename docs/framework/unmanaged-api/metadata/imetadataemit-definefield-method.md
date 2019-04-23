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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8ba8a762c56a666c67b25b9ce0420099fce419a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223527"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="26952-102">IMetaDataEmit::DefineField — Metoda</span><span class="sxs-lookup"><span data-stu-id="26952-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="26952-103">Tworzy definicję dla pola przy użyciu podpisu określonych metadanych, a następnie pobiera token do tej definicji pola.</span><span class="sxs-lookup"><span data-stu-id="26952-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26952-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26952-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="26952-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26952-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="26952-106">[in] `mdTypeDef` Tokenu dla otaczającej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="26952-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="26952-107">[in] Nazwa pola w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="26952-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="26952-108">[in] Atrybuty pól.</span><span class="sxs-lookup"><span data-stu-id="26952-108">[in] The field attributes.</span></span> <span data-ttu-id="26952-109">Jest to z `CorFieldAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="26952-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="26952-110">[in] Podpis pola jako obiekt BLOB.</span><span class="sxs-lookup"><span data-stu-id="26952-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="26952-111">[in] Liczba bajtów w `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="26952-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="26952-112">[in] `ELEMENT_TYPE_` *\** Wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="26952-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="26952-113">Jest to `CorElementType` wartość.</span><span class="sxs-lookup"><span data-stu-id="26952-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="26952-114">Jeśli nie definiuje stałą wartość dla pola, użyj `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="26952-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="26952-115">[in] Stała wartość dla pola.</span><span class="sxs-lookup"><span data-stu-id="26952-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="26952-116">[in] Rozmiar w znakach (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="26952-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="26952-117">[out] `mdFieldDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="26952-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26952-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26952-118">Requirements</span></span>  
 <span data-ttu-id="26952-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26952-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26952-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="26952-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26952-121">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26952-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26952-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26952-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26952-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26952-123">See also</span></span>

- [<span data-ttu-id="26952-124">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="26952-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="26952-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="26952-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
