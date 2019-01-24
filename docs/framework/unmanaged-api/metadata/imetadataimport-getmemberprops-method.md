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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98d7be5adc81cff09b121265e7d5b5f712122607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611413"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="be9aa-102">IMetaDataImport::GetMemberProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="be9aa-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="be9aa-103">Pobiera informacje o metadanych, w tym m.in. nazwy, podpis binarny i względny adres wirtualny, <xref:System.Type> odwołuje się token metadanych określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="be9aa-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be9aa-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="be9aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be9aa-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="be9aa-106">[in] Token, który odwołuje się do elementu członkowskiego, który można pobrać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="be9aa-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="be9aa-107">[out] Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="be9aa-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="be9aa-108">[out] Nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="be9aa-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="be9aa-109">[in] Rozmiar w znaków `szMember` buforu.</span><span class="sxs-lookup"><span data-stu-id="be9aa-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="be9aa-110">[out] Rozmiar w znaki dwubajtowe zwrócone nazwy.</span><span class="sxs-lookup"><span data-stu-id="be9aa-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="be9aa-111">[out] Wartości flagi zastosowane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="be9aa-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="be9aa-112">[out] Wskaźnik do podpisu binarne metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="be9aa-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="be9aa-113">[out] Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="be9aa-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="be9aa-114">[out] Wskaźnik do wirtualnej adres względny elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="be9aa-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="be9aa-115">[out] Wszystkie skojarzone z elementem flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="be9aa-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="be9aa-116">[out] Flaga, która oznacza <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="be9aa-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="be9aa-117">[out] Wartość stała ciągu zwracane przez ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="be9aa-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="be9aa-118">[out] Rozmiar w znakach `ppValue`, lub zero, jeśli `ppValue` nie zawiera ciągu.</span><span class="sxs-lookup"><span data-stu-id="be9aa-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be9aa-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be9aa-119">Requirements</span></span>  
 <span data-ttu-id="be9aa-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be9aa-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be9aa-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="be9aa-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be9aa-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be9aa-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be9aa-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be9aa-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be9aa-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be9aa-124">See also</span></span>
- [<span data-ttu-id="be9aa-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="be9aa-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="be9aa-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="be9aa-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
