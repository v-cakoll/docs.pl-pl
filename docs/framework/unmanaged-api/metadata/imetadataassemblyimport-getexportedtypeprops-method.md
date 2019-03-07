---
title: IMetaDataAssemblyImport::GetExportedTypeProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 930c78386eca5a2a9b8662129c1470f6170aed77
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478534"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="27d30-102">IMetaDataAssemblyImport::GetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="27d30-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="27d30-103">Pobiera zestaw właściwości typu wyeksportowanego za pomocą podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="27d30-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27d30-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27d30-104">Syntax</span></span>  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27d30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27d30-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="27d30-106">[in] `mdExportedType` Token metadanych, który reprezentuje typ eksportowany.</span><span class="sxs-lookup"><span data-stu-id="27d30-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="27d30-107">[out] Nazwa typu wyeksportowanego.</span><span class="sxs-lookup"><span data-stu-id="27d30-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="27d30-108">[in] Rozmiar w szerokich znaków z `szName`.</span><span class="sxs-lookup"><span data-stu-id="27d30-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="27d30-109">[out] Liczba znaków dwubajtowych rzeczywistego zwrotu w `szName`</span><span class="sxs-lookup"><span data-stu-id="27d30-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="27d30-110">[out] `mdFile`, `mdAssemblyRef`, Lub `mdExportedType` token metadanych, który zawiera lub zezwala na dostęp do właściwości wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="27d30-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="27d30-111">[out] Wskaźnik do `mdTypeDef` token, który reprezentuje typ w pliku.</span><span class="sxs-lookup"><span data-stu-id="27d30-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="27d30-112">[out] Wskaźnik flagi, które opisują metadane stosowane do wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="27d30-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="27d30-113">Wartość flagi może być co najmniej jeden [cortypeattr —](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="27d30-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27d30-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27d30-114">Requirements</span></span>  
 <span data-ttu-id="27d30-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27d30-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27d30-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="27d30-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27d30-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27d30-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27d30-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27d30-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d30-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27d30-119">See also</span></span>
- [<span data-ttu-id="27d30-120">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="27d30-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
