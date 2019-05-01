---
title: IMetaDataImport::GetParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ac8efed8c0a905d2cfad433348a99fe578eeae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777629"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="036c7-102">IMetaDataImport::GetParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="036c7-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="036c7-103">Pobiera metadane wartości dla parametru odwołuje się określona ParamDef token.</span><span class="sxs-lookup"><span data-stu-id="036c7-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="036c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="036c7-104">Syntax</span></span>  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="036c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="036c7-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="036c7-106">[in] Token ParamDef, który reprezentuje parametr można zwrócić metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="036c7-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="036c7-107">[out] Wskaźnik do tokenu MethodDef reprezentujący metodę, która przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="036c7-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="036c7-108">[out] Numer porządkowy pozycja parametru na liście argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="036c7-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="036c7-109">[out] Bufor do przechowywania nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="036c7-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="036c7-110">[in] Żądany rozmiar w znaków `szName`.</span><span class="sxs-lookup"><span data-stu-id="036c7-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="036c7-111">[out] Rozmiar zwrócony w znaków `szName`.</span><span class="sxs-lookup"><span data-stu-id="036c7-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="036c7-112">[out] Wskaźnik do flag atrybut skojarzony z parametrem.</span><span class="sxs-lookup"><span data-stu-id="036c7-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="036c7-113">Jest to z `CorParamAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="036c7-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="036c7-114">[out] Wskaźnik do określania flagi, że parametr jest <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="036c7-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="036c7-115">[out] Wskaźnik ze stałym ciągiem zwrócone przez parametr.</span><span class="sxs-lookup"><span data-stu-id="036c7-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="036c7-116">[out] Rozmiar `ppValue` znaków dwubajtowych lub zero, jeśli `ppValue` nie zawiera ciągu.</span><span class="sxs-lookup"><span data-stu-id="036c7-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="036c7-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="036c7-117">Remarks</span></span>

<span data-ttu-id="036c7-118">Sekwencja wartości w `pulSequence` zaczynają się od 1 dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="036c7-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="036c7-119">Wartość zwracana ma kolejny numer 0.</span><span class="sxs-lookup"><span data-stu-id="036c7-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="036c7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="036c7-120">Requirements</span></span>  
 <span data-ttu-id="036c7-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="036c7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036c7-122">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="036c7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="036c7-123">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="036c7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="036c7-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036c7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036c7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="036c7-125">See also</span></span>

- [<span data-ttu-id="036c7-126">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="036c7-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="036c7-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="036c7-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
