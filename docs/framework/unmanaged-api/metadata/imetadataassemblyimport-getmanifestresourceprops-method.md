---
title: "IMetaDataAssemblyImport::GetManifestResourceProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetManifestResourceProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ba9af4abca111b94a678c48d236a53dc6313b21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="009cd-102">IMetaDataAssemblyImport::GetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="009cd-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="009cd-103">Pobiera zestaw właściwości zasobu manifestu o sygnaturze określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="009cd-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="009cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="009cd-104">Syntax</span></span>  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="009cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="009cd-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="009cd-106">[in] `mdManifestResource` Token reprezentujący zasobu, dla którego można pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="009cd-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="009cd-107">[out] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="009cd-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="009cd-108">[in] Rozmiar w znaki dwubajtowe z `szName`.</span><span class="sxs-lookup"><span data-stu-id="009cd-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="009cd-109">[out] Wskaźnik do liczby znaki dwubajtowe faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="009cd-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="009cd-110">[out] Wskaźnik do `mdFile` tokenu lub `mdAssemblyRef` token reprezentujący pliku lub zestawu, który zawiera zasób.</span><span class="sxs-lookup"><span data-stu-id="009cd-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="009cd-111">[out] Wskaźnik do wartość określa Przesunięcie początku zasobów w pliku.</span><span class="sxs-lookup"><span data-stu-id="009cd-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="009cd-112">[out] Wskaźnik do flagi opisujące metadanych dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="009cd-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="009cd-113">Wartość flagi składa się z co najmniej jeden [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="009cd-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="009cd-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="009cd-114">Requirements</span></span>  
 <span data-ttu-id="009cd-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="009cd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="009cd-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="009cd-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="009cd-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="009cd-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="009cd-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="009cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009cd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="009cd-119">See Also</span></span>  
 [<span data-ttu-id="009cd-120">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="009cd-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
