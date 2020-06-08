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
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503643"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="d3b8e-102">IMetaDataImport::GetMemberProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3b8e-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="d3b8e-103">Pobiera informacje przechowywane w metadanych dla określonej definicji elementu członkowskiego, w tym nazwę, podpis binarny i względny adres wirtualny, do <xref:System.Type> elementu członkowskiego, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="d3b8e-104">Jest to prosta metoda pomocnicza: Jeśli *MB* jest elementem MethodDef, **GetMethodProps —** jest wywoływana; Jeśli liczba *MB* to FieldDef, **GetFieldProps —** jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="d3b8e-105">Zobacz te inne metody, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="d3b8e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3b8e-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d3b8e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3b8e-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="d3b8e-108">podczas Token, który odwołuje się do elementu członkowskiego, aby uzyskać skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d3b8e-109">określoną Wskaźnik do tokenu metadanych, który reprezentuje klasę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="d3b8e-110">określoną Nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="d3b8e-111">podczas Rozmiar w postaci znaków dwubajtowych w `szMember` buforze.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="d3b8e-112">określoną Rozmiar w postaci znaków dwubajtowych zwracanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="d3b8e-113">określoną Wszystkie wartości flag zastosowane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="d3b8e-114">określoną Wskaźnik do binarnego podpisu metadanych elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="d3b8e-115">określoną Rozmiar w bajtach `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="d3b8e-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="d3b8e-116">określoną Wskaźnik do względnego adresu wirtualnego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="d3b8e-117">określoną Wszystkie flagi implementacji metody skojarzone z elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="d3b8e-118">określoną Flaga oznaczająca element <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="d3b8e-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="d3b8e-119">Jest to jedna z `ELEMENT_TYPE_*` wartości.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="d3b8e-120">określoną Wartość stałej ciągu zwrócona przez ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="d3b8e-121">określoną Rozmiar w znakach `ppValue` lub zero, jeśli nie zawiera `ppValue` ciągu.</span><span class="sxs-lookup"><span data-stu-id="d3b8e-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3b8e-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3b8e-122">Requirements</span></span>  
 <span data-ttu-id="d3b8e-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3b8e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b8e-124">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d3b8e-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3b8e-125">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3b8e-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3b8e-126">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3b8e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b8e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3b8e-127">See also</span></span>

- [<span data-ttu-id="d3b8e-128">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3b8e-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d3b8e-129">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3b8e-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
