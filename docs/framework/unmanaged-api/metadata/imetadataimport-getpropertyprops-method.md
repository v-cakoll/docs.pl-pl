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
ms.openlocfilehash: cac5aaa7ed13b6a48b36ad550da8b73d0deb2ee7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491046"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="96b52-102">IMetaDataImport::GetPropertyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="96b52-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="96b52-103">Pobiera metadane dla właściwości reprezentowanej przez określony token.</span><span class="sxs-lookup"><span data-stu-id="96b52-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96b52-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="96b52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96b52-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="96b52-106">podczas Token reprezentujący właściwość, dla której ma zostać zwrócona wartość metadanych.</span><span class="sxs-lookup"><span data-stu-id="96b52-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="96b52-107">określoną Wskaźnik do tokenu TypeDef, który reprezentuje typ implementujący właściwość.</span><span class="sxs-lookup"><span data-stu-id="96b52-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="96b52-108">określoną Bufor służący do przechowywania nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b52-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="96b52-109">podczas Rozmiar w postaci znaków dwubajtowych `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="96b52-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="96b52-110">określoną Liczba znaków dwubajtowych zwracana w `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="96b52-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="96b52-111">określoną Wskaźnik do dowolnych flag atrybutów zastosowanych do właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b52-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="96b52-112">Ta wartość jest maska bitowa z wyliczenia [CorPropertyAttr —](corpropertyattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="96b52-112">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="96b52-113">określoną Wskaźnik do sygnatury metadanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b52-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="96b52-114">określoną Liczba bajtów zwróconych w `ppvSig` .</span><span class="sxs-lookup"><span data-stu-id="96b52-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="96b52-115">określoną Flaga określająca typ stałej, która jest wartością domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b52-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="96b52-116">Ta wartość pochodzi z wyliczenia CorElementType —.</span><span class="sxs-lookup"><span data-stu-id="96b52-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="96b52-117">określoną Wskaźnik do bajtów przechowujących wartość domyślną dla tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b52-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="96b52-118">określoną Rozmiar w postaci znaków dwubajtowych `ppDefaultValue` , jeśli `pdwCPlusTypeFlag` jest ELEMENT_TYPE_STRING; w przeciwnym razie ta wartość nie jest istotna.</span><span class="sxs-lookup"><span data-stu-id="96b52-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="96b52-119">W takim przypadku długość `ppDefaultValue` jest wywnioskowana z typu, który jest określony przez `pdwCPlusTypeFlag` .</span><span class="sxs-lookup"><span data-stu-id="96b52-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="96b52-120">określoną Wskaźnik do tokenu MethodDef, który reprezentuje metodę dostępu set dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b52-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="96b52-121">określoną Wskaźnik do tokenu MethodDef, który reprezentuje metodę get akcesora dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="96b52-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="96b52-122">określoną Tablica tokenów MethodDef, która reprezentuje inne metody skojarzone z właściwością.</span><span class="sxs-lookup"><span data-stu-id="96b52-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="96b52-123">podczas Maksymalny rozmiar `rmdOtherMethod` tablicy.</span><span class="sxs-lookup"><span data-stu-id="96b52-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="96b52-124">Jeśli tablica nie jest wystarczająco duża, aby pomieścić wszystkie metody, są one pomijane bez ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="96b52-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="96b52-125">określoną Liczba tokenów MethodDef zwróconych w `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="96b52-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b52-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96b52-126">Requirements</span></span>  
 <span data-ttu-id="96b52-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b52-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b52-128">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="96b52-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96b52-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="96b52-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96b52-130">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b52-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b52-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96b52-131">See also</span></span>

- [<span data-ttu-id="96b52-132">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="96b52-132">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="96b52-133">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="96b52-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
