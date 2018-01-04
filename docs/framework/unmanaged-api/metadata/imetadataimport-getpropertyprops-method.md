---
title: "IMetaDataImport::GetPropertyProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d838f43b500ac3dd0c3b44d9d84dd9fc039c6e16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="b91ef-102">IMetaDataImport::GetPropertyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b91ef-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="b91ef-103">Pobiera metadane dla właściwości reprezentowanej przez określony token.</span><span class="sxs-lookup"><span data-stu-id="b91ef-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b91ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b91ef-104">Syntax</span></span>  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b91ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b91ef-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="b91ef-106">[in] Token, który reprezentuje właściwość do zwracania metadanych.</span><span class="sxs-lookup"><span data-stu-id="b91ef-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b91ef-107">[out] Wskaźnik do TypeDef token, który reprezentuje typ, który implementuje właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="b91ef-108">[out] Bufor do przechowywania nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="b91ef-109">[in] Rozmiar w znaki dwubajtowe `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="b91ef-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="b91ef-110">[out] Liczba zwracanych w znaki dwubajtowe `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="b91ef-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="b91ef-111">[out] Wskaźnik do flagi, atrybut zastosowany do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="b91ef-112">Ta wartość jest maską bitów z [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b91ef-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="b91ef-113">[out] Wskaźnik do podpisania metadanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="b91ef-114">[out] Liczba bajtów zwrócona w `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="b91ef-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="b91ef-115">[out] Flaga określający typ stałej, która jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="b91ef-116">Ta wartość jest z corelementtype — wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="b91ef-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="b91ef-117">[out] Wskaźnik do bajtów, które przechowują wartość domyślna dla tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="b91ef-118">[out] Rozmiar w znaki dwubajtowe `ppDefaultValue`, jeśli `pdwCPlusTypeFlag` jest ELEMENT_TYPE_STRING; w przeciwnym razie wartość ta nie jest ważna.</span><span class="sxs-lookup"><span data-stu-id="b91ef-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="b91ef-119">W takim przypadku długość `ppDefaultValue` jest wywnioskowany na podstawie typu, który jest określony przez `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="b91ef-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="b91ef-120">[out] Wskaźnik do tokenu MethodDef, który reprezentuje metody dostępu set dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="b91ef-121">[out] Wskaźnik do tokenu MethodDef, który reprezentuje metodę dostępu get dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="b91ef-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="b91ef-122">[out] Tablica MethodDef reprezentujących innych metod skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="b91ef-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b91ef-123">[in] Maksymalny rozmiar `rmdOtherMethod` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b91ef-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="b91ef-124">Tablica jest wystarczająco duży, aby pomieścić wszystkie metody nie zostaną podane, są pominięcie bez ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="b91ef-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="b91ef-125">[out] Liczba tokenów MethodDef zwracane w `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b91ef-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91ef-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b91ef-126">Requirements</span></span>  
 <span data-ttu-id="b91ef-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b91ef-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91ef-128">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b91ef-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b91ef-129">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b91ef-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b91ef-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91ef-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91ef-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b91ef-131">See Also</span></span>  
 [<span data-ttu-id="b91ef-132">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b91ef-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b91ef-133">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b91ef-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
