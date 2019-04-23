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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200808"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="f34f0-102">IMetaDataImport::GetMemberProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="f34f0-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="f34f0-103">Pobiera informacje przechowywane w metadanych dla definicji określonego elementu członkowskiego, w tym m.in. nazwy, podpis binarny i względny adres wirtualny, <xref:System.Type> odwołuje się token metadanych określonego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f34f0-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="f34f0-104">Jest to metoda pomocnika proste: Jeśli *mb* jest MethodDef **getmethodprops —** nosi nazwę; Jeśli *mb* jest FieldDef **getfieldprops —** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="f34f0-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="f34f0-105">Zobacz te inne metody, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="f34f0-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="f34f0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f34f0-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f34f0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f34f0-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="f34f0-108">[in] Token, który odwołuje się do elementu członkowskiego, który można pobrać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="f34f0-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f34f0-109">[out] Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f34f0-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="f34f0-110">[out] Nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f34f0-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="f34f0-111">[in] Rozmiar w znaków `szMember` buforu.</span><span class="sxs-lookup"><span data-stu-id="f34f0-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="f34f0-112">[out] Rozmiar w znaki dwubajtowe zwrócone nazwy.</span><span class="sxs-lookup"><span data-stu-id="f34f0-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="f34f0-113">[out] Wartości flagi zastosowane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f34f0-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="f34f0-114">[out] Wskaźnik do podpisu binarne metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f34f0-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="f34f0-115">[out] Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="f34f0-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="f34f0-116">[out] Wskaźnik do wirtualnej adres względny elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f34f0-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="f34f0-117">[out] Wszystkie skojarzone z elementem flagi implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="f34f0-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="f34f0-118">[out] Flaga, która oznacza <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="f34f0-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="f34f0-119">Jest to jeden z `ELEMENT_TYPE_*` wartości.</span><span class="sxs-lookup"><span data-stu-id="f34f0-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="f34f0-120">[out] Wartość stała ciągu zwracane przez ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="f34f0-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="f34f0-121">[out] Rozmiar w znakach `ppValue`, lub zero, jeśli `ppValue` nie zawiera ciągu.</span><span class="sxs-lookup"><span data-stu-id="f34f0-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f34f0-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f34f0-122">Requirements</span></span>  
 <span data-ttu-id="f34f0-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f34f0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f34f0-124">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f34f0-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f34f0-125">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f34f0-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f34f0-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f34f0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f34f0-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f34f0-127">See also</span></span>

- [<span data-ttu-id="f34f0-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="f34f0-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f34f0-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f34f0-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
