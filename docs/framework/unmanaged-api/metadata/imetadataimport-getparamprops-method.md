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
ms.openlocfilehash: 95850448504fd863f2726a7fb7574436476a6dc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449328"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="2b0a3-102">IMetaDataImport::GetParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b0a3-102">IMetaDataImport::GetParamProps Method</span></span>
<span data-ttu-id="2b0a3-103">Pobiera wartości metadanych dla parametru odwołuje się określony ParamDef token.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-103">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b0a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b0a3-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2b0a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b0a3-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2b0a3-106">[in] Token ParamDef, który reprezentuje parametr do zwracania metadanych.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-106">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="2b0a3-107">[out] Wskaźnik do tokenu MethodDef reprezentujący metodę, która przyjmuje parametr.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-107">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="2b0a3-108">[out] {Numer porządkowy pozycja parametru na liście argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-108">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="2b0a3-109">[out] Bufor aby pomieścić nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-109">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2b0a3-110">[in] Żądany rozmiar w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2b0a3-111">[out] Rozmiar zwróconego w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="2b0a3-112">[out] Wskaźnik do żadnych flag atrybutów skojarzonych z parametrem.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-112">[out] A pointer to any attribute flags associated with the parameter.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="2b0a3-113">[out] Wskaźnik do określania flagi, że parametr jest <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-113">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="2b0a3-114">[out] Wskaźnik ze stałym ciągiem zwrócona przez parametr.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-114">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="2b0a3-115">[out] Rozmiar `ppValue` w znaki dwubajtowe lub zero, jeśli `ppValue` nie zawiera ciąg.</span><span class="sxs-lookup"><span data-stu-id="2b0a3-115">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b0a3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b0a3-116">Requirements</span></span>  
 <span data-ttu-id="2b0a3-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b0a3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b0a3-118">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b0a3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b0a3-119">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b0a3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b0a3-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b0a3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b0a3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b0a3-121">See Also</span></span>  
 [<span data-ttu-id="2b0a3-122">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b0a3-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="2b0a3-123">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b0a3-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
