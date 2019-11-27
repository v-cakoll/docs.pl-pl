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
ms.openlocfilehash: bb73ccdd9eee4b5a655a56b5d6757e0c6003fbc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437126"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="b4cc1-102">IMetaDataImport::GetParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4cc1-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="b4cc1-103">Pobiera wartości metadanych dla parametru, do którego odwołuje się określony token ParamDef.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4cc1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4cc1-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="b4cc1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4cc1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b4cc1-106">podczas Token ParamDef reprezentujący parametr, dla którego mają zostać zwrócone metadane.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="b4cc1-107">określoną Wskaźnik do tokenu MethodDef reprezentujący metodę, która pobiera parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="b4cc1-108">określoną Pozycja porządkowa parametru na liście argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="b4cc1-109">określoną Bufor służący do przechowywania nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b4cc1-110">podczas Żądany rozmiar w szerokich znakach `szName`.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b4cc1-111">określoną Zwrócony rozmiar w szerokich znakach `szName`.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="b4cc1-112">określoną Wskaźnik do dowolnych flag atrybutów skojarzonych z parametrem.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-112">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="b4cc1-113">To jest maska bitów wartości `CorParamAttr`.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-113">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="b4cc1-114">określoną Wskaźnik do flagi określającej, że parametr jest <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-114">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b4cc1-115">określoną Wskaźnik do stałego ciągu zwracanego przez parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-115">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="b4cc1-116">określoną Rozmiar `ppValue` w postaci dwubajtowej lub zero, jeśli `ppValue` nie zawiera ciągu.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-116">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4cc1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4cc1-117">Remarks</span></span>

<span data-ttu-id="b4cc1-118">Wartości sekwencji w `pulSequence` zaczynają się od 1 dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-118">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="b4cc1-119">Wartość zwracana ma numer sekwencyjny równy 0.</span><span class="sxs-lookup"><span data-stu-id="b4cc1-119">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4cc1-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4cc1-120">Requirements</span></span>  
 <span data-ttu-id="b4cc1-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4cc1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4cc1-122">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b4cc1-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4cc1-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b4cc1-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b4cc1-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4cc1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4cc1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4cc1-125">See also</span></span>

- [<span data-ttu-id="b4cc1-126">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4cc1-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b4cc1-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4cc1-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
