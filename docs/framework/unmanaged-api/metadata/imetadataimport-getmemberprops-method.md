---
title: "IMetaDataImport::GetMemberProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b52d3130400310379c69eb0202217d1cd37ff18d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="60f1f-102">IMetaDataImport::GetMemberProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="60f1f-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="60f1f-103">Pobiera informacje o metadanych, łącznie z nazwą, podpis binarny i wirtualny adres względny elementu <xref:System.Type> odwołuje się token metadanych określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="60f1f-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60f1f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="60f1f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60f1f-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="60f1f-106">[in] Token, który odwołuje się do elementu członkowskiego do pobrania skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="60f1f-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="60f1f-107">[out] Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="60f1f-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="60f1f-108">[out] Nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="60f1f-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="60f1f-109">[in] Rozmiar w znaki dwubajtowe `szMember` buforu.</span><span class="sxs-lookup"><span data-stu-id="60f1f-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="60f1f-110">[out] Rozmiar w znaki dwubajtowe zwrócony nazwy.</span><span class="sxs-lookup"><span data-stu-id="60f1f-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="60f1f-111">[out] Wartości flagi zastosowany do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="60f1f-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="60f1f-112">[out] Wskaźnik do sygnatury binarne metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="60f1f-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="60f1f-113">[out] Wyrażony w bajtach rozmiar `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="60f1f-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="60f1f-114">[out] Wskaźnik do wirtualnego adres względny elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="60f1f-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="60f1f-115">[out] Wszystkie skojarzone z danym elementem flagi implementacji metod.</span><span class="sxs-lookup"><span data-stu-id="60f1f-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="60f1f-116">[out] Flaga, która oznacza <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="60f1f-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="60f1f-117">[out] Wartość stałej ciągu zwróconych przez ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="60f1f-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="60f1f-118">[out] Rozmiar w znakach `ppValue`, lub zero, jeśli `ppValue` nie zawiera ciąg.</span><span class="sxs-lookup"><span data-stu-id="60f1f-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f1f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60f1f-119">Requirements</span></span>  
 <span data-ttu-id="60f1f-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f1f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f1f-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="60f1f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60f1f-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60f1f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60f1f-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f1f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f1f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60f1f-124">See Also</span></span>  
 [<span data-ttu-id="60f1f-125">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="60f1f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="60f1f-126">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="60f1f-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
