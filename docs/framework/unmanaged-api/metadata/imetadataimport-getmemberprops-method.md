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
ms.openlocfilehash: 83dec9b6ed3b1e538e0f1b7d13a33b8bdbc1cf54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777731"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="9a9b9-102">IMetaDataImport::GetMemberProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a9b9-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="9a9b9-103">Pobiera informacje przechowywane w metadanych dla definicji określonego elementu członkowskiego, w tym m.in. nazwy, podpis binarny i względny adres wirtualny, <xref:System.Type> odwołuje się token metadanych określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="9a9b9-104">Jest to metoda pomocnika proste: Jeśli *mb* jest MethodDef **getmethodprops —** nosi nazwę; Jeśli *mb* jest FieldDef **getfieldprops —** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="9a9b9-105">Zobacz te inne metody, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="9a9b9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a9b9-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9a9b9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a9b9-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="9a9b9-108">[in] Token, który odwołuje się do elementu członkowskiego, który można pobrać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="9a9b9-109">[out] Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="9a9b9-110">[out] Nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="9a9b9-111">[in] Rozmiar w znaków `szMember` buforu.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="9a9b9-112">[out] Rozmiar w znaki dwubajtowe zwrócone nazwy.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="9a9b9-113">[out] Wartości flagi zastosowane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="9a9b9-114">[out] Wskaźnik do podpisu binarne metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="9a9b9-115">[out] Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="9a9b9-116">[out] Wskaźnik do wirtualnej adres względny elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="9a9b9-117">[out] Wszystkie skojarzone z elementem flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="9a9b9-118">[out] Flaga, która oznacza <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="9a9b9-119">Jest to jeden z `ELEMENT_TYPE_*` wartości.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="9a9b9-120">[out] Wartość stała ciągu zwracane przez ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="9a9b9-121">[out] Rozmiar w znakach `ppValue`, lub zero, jeśli `ppValue` nie zawiera ciągu.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a9b9-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a9b9-122">Requirements</span></span>  
 <span data-ttu-id="9a9b9-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a9b9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a9b9-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9a9b9-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a9b9-125">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a9b9-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a9b9-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a9b9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a9b9-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a9b9-127">See also</span></span>

- [<span data-ttu-id="9a9b9-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a9b9-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9a9b9-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9a9b9-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
