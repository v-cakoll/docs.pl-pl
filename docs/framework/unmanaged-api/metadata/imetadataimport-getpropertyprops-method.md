---
title: IMetaDataImport::GetPropertyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175333"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="348b6-102">IMetaDataImport::GetPropertyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="348b6-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="348b6-103">Pobiera metadane dla właściwości reprezentowane przez określony token.</span><span class="sxs-lookup"><span data-stu-id="348b6-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="348b6-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="348b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="348b6-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="348b6-106">[w] Token, który reprezentuje właściwość do zwrócenia metadanych.</span><span class="sxs-lookup"><span data-stu-id="348b6-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="348b6-107">[na zewnątrz] Wskaźnik do TypeDef token, który reprezentuje typ, który implementuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="348b6-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="348b6-108">[na zewnątrz] Bufor do przechowywania nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="348b6-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="348b6-109">[w] Rozmiar w szerokich `szProperty`znaków .</span><span class="sxs-lookup"><span data-stu-id="348b6-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="348b6-110">[na zewnątrz] Liczba szerokich znaków `szProperty`zwróconych w pliku .</span><span class="sxs-lookup"><span data-stu-id="348b6-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="348b6-111">[na zewnątrz] Wskaźnik do wszystkich flag atrybutów stosowanych do właściwości.</span><span class="sxs-lookup"><span data-stu-id="348b6-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="348b6-112">Ta wartość jest maską bitową z [wyliczenia CorPropertyAttr.](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="348b6-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="348b6-113">[na zewnątrz] Wskaźnik do podpisu metadanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="348b6-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="348b6-114">[na zewnątrz] Liczba bajtów zwróconych w `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="348b6-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="348b6-115">[na zewnątrz] Flaga określająca typ stałej, która jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="348b6-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="348b6-116">Ta wartość jest z wyliczenia CorElementType.</span><span class="sxs-lookup"><span data-stu-id="348b6-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="348b6-117">[na zewnątrz] Wskaźnik do bajtów, które przechowują wartość domyślną dla tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="348b6-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="348b6-118">[na zewnątrz] Rozmiar w szerokich `ppDefaultValue`znakach , jeśli `pdwCPlusTypeFlag` jest ELEMENT_TYPE_STRING; w przeciwnym razie wartość ta nie jest istotna.</span><span class="sxs-lookup"><span data-stu-id="348b6-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="348b6-119">W takim przypadku długość `ppDefaultValue` jest wywnioskowana z `pdwCPlusTypeFlag`typu określonego przez .</span><span class="sxs-lookup"><span data-stu-id="348b6-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="348b6-120">[na zewnątrz] Wskaźnik do MethodDef token, który reprezentuje metodę akcesora zestawu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="348b6-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="348b6-121">[na zewnątrz] Wskaźnik do MethodDef token, który reprezentuje get metody akcesora dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="348b6-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="348b6-122">[na zewnątrz] Tablica tokenów MethodDef, które reprezentują inne metody skojarzone z właściwością.</span><span class="sxs-lookup"><span data-stu-id="348b6-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="348b6-123">[w] Maksymalny rozmiar `rmdOtherMethod` tablicy.</span><span class="sxs-lookup"><span data-stu-id="348b6-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="348b6-124">Jeśli nie podasz tablicy wystarczająco duże, aby pomieścić wszystkie metody, są pomijane bez ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="348b6-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="348b6-125">[na zewnątrz] Liczba tokenów MethodDef zwrócona w `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="348b6-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="348b6-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="348b6-126">Requirements</span></span>  
 <span data-ttu-id="348b6-127">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="348b6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="348b6-128">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="348b6-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="348b6-129">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="348b6-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="348b6-130">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="348b6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348b6-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="348b6-131">See also</span></span>

- [<span data-ttu-id="348b6-132">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="348b6-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="348b6-133">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="348b6-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
