---
title: "IMetaDataAssemblyImport::GetAssemblyProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e99474fea329f53286d698d0e1a302909d5cc65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="80a6b-102">IMetaDataAssemblyImport::GetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="80a6b-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="80a6b-103">Pobiera zbiór właściwości dla zestawu z podpisem określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="80a6b-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80a6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80a6b-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80a6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80a6b-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="80a6b-106">[in].</span><span class="sxs-lookup"><span data-stu-id="80a6b-106">[in].</span></span> <span data-ttu-id="80a6b-107">`mdAssembly` Token metadanych, który reprezentuje zestaw, do którego można pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="80a6b-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="80a6b-108">[out] Wskaźnik do klucza publicznego lub token metadanych.</span><span class="sxs-lookup"><span data-stu-id="80a6b-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="80a6b-109">[out] Liczba bajtów zwróconych klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="80a6b-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="80a6b-110">[out] Wskaźnik do algorytm wyznaczania wartości skrótu plików w zestawie.</span><span class="sxs-lookup"><span data-stu-id="80a6b-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="80a6b-111">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="80a6b-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="80a6b-112">[in] Rozmiar w znaki dwubajtowe z `szName`.</span><span class="sxs-lookup"><span data-stu-id="80a6b-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="80a6b-113">[out] Liczba znaki dwubajtowe faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="80a6b-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="80a6b-114">[out] Wskaźnik do struktury assemblymetadata — zawierający metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="80a6b-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="80a6b-115">[out] Flagi opisujące metadanych zastosowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="80a6b-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="80a6b-116">Ta wartość jest kombinacją co najmniej jeden [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="80a6b-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80a6b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80a6b-117">Requirements</span></span>  
 <span data-ttu-id="80a6b-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80a6b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80a6b-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80a6b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80a6b-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80a6b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80a6b-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80a6b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a6b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80a6b-122">See Also</span></span>  
 [<span data-ttu-id="80a6b-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="80a6b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
