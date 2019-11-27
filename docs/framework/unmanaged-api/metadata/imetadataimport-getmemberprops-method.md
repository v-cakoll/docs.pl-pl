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
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437514"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="d5cea-102">IMetaDataImport::GetMemberProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="d5cea-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="d5cea-103">Pobiera informacje przechowywane w metadanych dla określonej definicji elementu członkowskiego, w tym nazwę, podpis binarny i względny adres wirtualny, elementu członkowskiego <xref:System.Type>, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="d5cea-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="d5cea-104">Jest to prosta metoda pomocnicza: Jeśli *MB* jest elementem MethodDef, **GetMethodProps —** jest wywoływana; Jeśli liczba *MB* to FieldDef, **GetFieldProps —** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d5cea-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="d5cea-105">Zobacz te inne metody, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="d5cea-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="d5cea-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5cea-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d5cea-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5cea-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="d5cea-108">podczas Token, który odwołuje się do elementu członkowskiego, aby uzyskać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="d5cea-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d5cea-109">określoną Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d5cea-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="d5cea-110">określoną Nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d5cea-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="d5cea-111">podczas Rozmiar w postaci znaków dwubajtowych bufora `szMember`.</span><span class="sxs-lookup"><span data-stu-id="d5cea-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="d5cea-112">określoną Rozmiar w postaci znaków dwubajtowych zwracanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d5cea-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="d5cea-113">określoną Wszystkie wartości flag zastosowane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d5cea-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="d5cea-114">określoną Wskaźnik do binarnego podpisu metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d5cea-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="d5cea-115">określoną Rozmiar w bajtach `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="d5cea-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="d5cea-116">określoną Wskaźnik do względnego adresu wirtualnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d5cea-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="d5cea-117">określoną Wszystkie flagi implementacji metody skojarzone z elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="d5cea-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="d5cea-118">określoną Flaga oznaczająca <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="d5cea-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="d5cea-119">Jest to jedna z wartości `ELEMENT_TYPE_*`.</span><span class="sxs-lookup"><span data-stu-id="d5cea-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="d5cea-120">określoną Wartość stałej ciągu zwrócona przez ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="d5cea-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="d5cea-121">określoną Rozmiar w znakach `ppValue`lub zero, jeśli `ppValue` nie zawiera ciągu.</span><span class="sxs-lookup"><span data-stu-id="d5cea-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cea-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5cea-122">Requirements</span></span>  
 <span data-ttu-id="d5cea-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5cea-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cea-124">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d5cea-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5cea-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d5cea-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5cea-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cea-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5cea-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5cea-127">See also</span></span>

- [<span data-ttu-id="d5cea-128">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5cea-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d5cea-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5cea-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
