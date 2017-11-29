---
title: "IMetaDataEmit::DefineField — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2a544d7e676b71fb00b8fd7a3d871867f7f55626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="75c08-102">IMetaDataEmit::DefineField — Metoda</span><span class="sxs-lookup"><span data-stu-id="75c08-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="75c08-103">Tworzy definicję pola z podpisem określonych metadanych i pobiera token do tej definicji pola.</span><span class="sxs-lookup"><span data-stu-id="75c08-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75c08-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="75c08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75c08-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="75c08-106">[in] `mdTypeDef` Token otaczającej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75c08-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="75c08-107">[in] Nazwa pola w standardzie Unicode.</span><span class="sxs-lookup"><span data-stu-id="75c08-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="75c08-108">[in] Atrybuty pól.</span><span class="sxs-lookup"><span data-stu-id="75c08-108">[in] The field attributes.</span></span> <span data-ttu-id="75c08-109">To jest maską bitów z `CorFieldAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="75c08-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="75c08-110">[in] Podpis pola jako obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="75c08-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="75c08-111">[in] Liczba bajtów w `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="75c08-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="75c08-112">[in] `ELEMENT_TYPE_`  *\**  Wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="75c08-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="75c08-113">Jest to `CorElementType` wartość.</span><span class="sxs-lookup"><span data-stu-id="75c08-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="75c08-114">Jeśli nie definiuje wartości stałej dla pola, użyj `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="75c08-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="75c08-115">[in] Stała wartość dla pola.</span><span class="sxs-lookup"><span data-stu-id="75c08-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="75c08-116">[in] Rozmiar w znakach (Unicode) `pValue`.</span><span class="sxs-lookup"><span data-stu-id="75c08-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="75c08-117">[out] `mdFieldDef` Token przypisany.</span><span class="sxs-lookup"><span data-stu-id="75c08-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75c08-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75c08-118">Requirements</span></span>  
 <span data-ttu-id="75c08-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75c08-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75c08-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75c08-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75c08-121">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75c08-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75c08-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75c08-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c08-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75c08-123">See Also</span></span>  
 [<span data-ttu-id="75c08-124">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="75c08-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="75c08-125">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="75c08-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
