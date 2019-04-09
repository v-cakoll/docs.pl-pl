---
title: IMetaDataAssemblyImport::GetAssemblyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4817a62d276bfdb50bfcbf658f40f5568673bea0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163218"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="1dbe6-102">IMetaDataAssemblyImport::GetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="1dbe6-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="1dbe6-103">Pobiera zbiór właściwości dla zestawu podpisem określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dbe6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dbe6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1dbe6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dbe6-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="1dbe6-106">[in].</span><span class="sxs-lookup"><span data-stu-id="1dbe6-106">[in].</span></span> <span data-ttu-id="1dbe6-107">`mdAssembly` Token metadanych, który reprezentuje zestaw, dla którego można pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="1dbe6-108">[out] Wskaźnik do tokenu metadanych lub klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="1dbe6-109">[out] Liczba bajtów zwróconych klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="1dbe6-110">[out] Wskaźnik do algorytm wyznaczania wartości skrótu dla plików w zestawie.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="1dbe6-111">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1dbe6-112">[in] Rozmiar w szerokie znaki z `szName`.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1dbe6-113">[out] Liczba szerokie znaki rzeczywistego zwrotu w `szName`.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1dbe6-114">[out] Wskaźnik do assemblymetadata — struktura, która zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="1dbe6-115">[out] Flagi, które opisują metadane zastosowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="1dbe6-116">Ta wartość składa się z co najmniej jeden [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="1dbe6-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dbe6-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dbe6-117">Requirements</span></span>  
 <span data-ttu-id="1dbe6-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dbe6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dbe6-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1dbe6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dbe6-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1dbe6-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="1dbe6-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1dbe6-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1dbe6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dbe6-122">See also</span></span>

- [<span data-ttu-id="1dbe6-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1dbe6-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
