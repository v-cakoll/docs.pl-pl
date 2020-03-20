---
title: IMetaDataImport::GetMemberProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177227"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="ccfd4-102">IMetaDataImport::GetMemberProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ccfd4-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="ccfd4-103">Pobiera informacje przechowywane w metadanych dla definicji określonego elementu członkowskiego, w tym <xref:System.Type> nazwę, podpis binarny i względny adres wirtualny elementu członkowskiego, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="ccfd4-104">Jest to prosta metoda pomocnika: jeśli *mb* jest MethodDef, a następnie **GetMethodProps** jest wywoływana; jeśli *mb* jest FieldDef, a następnie **GetFieldProps** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="ccfd4-105">Zobacz te inne metody, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ccfd4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccfd4-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccfd4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccfd4-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="ccfd4-108">[w] Token, który odwołuje się do elementu członkowskiego, aby uzyskać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ccfd4-109">[na zewnątrz] Wskaźnik do tokenu metadanych, który reprezentuje klasę członka.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="ccfd4-110">[na zewnątrz] Nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="ccfd4-111">[w] Rozmiar w szerokich `szMember` znakach buforu.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="ccfd4-112">[na zewnątrz] Rozmiar w szerokich znakach zwracanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ccfd4-113">[na zewnątrz] Wszystkie wartości flag zastosowanych do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ccfd4-114">[na zewnątrz] Wskaźnik do podpisu binarnych metadanych członka.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ccfd4-115">[na zewnątrz] Rozmiar w bajtach . `ppvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="ccfd4-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="ccfd4-116">[na zewnątrz] Wskaźnik do względnego adresu wirtualnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="ccfd4-117">[na zewnątrz] Flagi implementacji dowolnej metody skojarzone z elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ccfd4-118">[na zewnątrz] Flaga oznaczająca <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="ccfd4-119">Jest to jedna `ELEMENT_TYPE_*` z wartości.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="ccfd4-120">[na zewnątrz] Stała wartość ciągu zwrócona przez ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="ccfd4-121">[na zewnątrz] Rozmiar znaków `ppValue`, lub zero, jeśli `ppValue` nie posiada ciągu.</span><span class="sxs-lookup"><span data-stu-id="ccfd4-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccfd4-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ccfd4-122">Requirements</span></span>  
 <span data-ttu-id="ccfd4-123">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccfd4-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccfd4-124">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ccfd4-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccfd4-125">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ccfd4-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccfd4-126">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccfd4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfd4-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccfd4-127">See also</span></span>

- [<span data-ttu-id="ccfd4-128">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ccfd4-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ccfd4-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ccfd4-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
