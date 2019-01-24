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
ms.openlocfilehash: c4e4b163cc783ccd01bc406789f5bf92448c697c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685532"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="00be3-102">IMetaDataImport::GetParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="00be3-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="00be3-103">Pobiera metadane wartości dla parametru odwołuje się określona ParamDef token.</span><span class="sxs-lookup"><span data-stu-id="00be3-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00be3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00be3-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="00be3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00be3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="00be3-106">[in] Token ParamDef, który reprezentuje parametr można zwrócić metadanych dla.</span><span class="sxs-lookup"><span data-stu-id="00be3-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="00be3-107">[out] Wskaźnik do tokenu MethodDef reprezentujący metodę, która przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="00be3-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="00be3-108">[out] Numer porządkowy pozycja parametru na liście argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="00be3-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="00be3-109">[out] Bufor do przechowywania nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="00be3-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="00be3-110">[in] Żądany rozmiar w znaków `szName`.</span><span class="sxs-lookup"><span data-stu-id="00be3-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="00be3-111">[out] Rozmiar zwrócony w znaków `szName`.</span><span class="sxs-lookup"><span data-stu-id="00be3-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="00be3-112">[out] Wskaźnik do flag atrybut skojarzony z parametrem.</span><span class="sxs-lookup"><span data-stu-id="00be3-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="00be3-113">[out] Wskaźnik do określania flagi, że parametr jest <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="00be3-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="00be3-114">[out] Wskaźnik ze stałym ciągiem zwrócone przez parametr.</span><span class="sxs-lookup"><span data-stu-id="00be3-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="00be3-115">[out] Rozmiar `ppValue` znaków dwubajtowych lub zero, jeśli `ppValue` nie zawiera ciągu.</span><span class="sxs-lookup"><span data-stu-id="00be3-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00be3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00be3-116">Requirements</span></span>  
 <span data-ttu-id="00be3-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00be3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00be3-118">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="00be3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00be3-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00be3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00be3-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00be3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00be3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00be3-121">See also</span></span>
- [<span data-ttu-id="00be3-122">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="00be3-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="00be3-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="00be3-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
