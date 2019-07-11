---
title: IMetaDataAssemblyImport::GetManifestResourceProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e47b1807e51427487d6af2f96ff5af437c4653eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760946"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="f1e82-102">IMetaDataAssemblyImport::GetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1e82-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="f1e82-103">Pobiera zestaw właściwości zasobu manifestu o podpisie określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="f1e82-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1e82-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="f1e82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1e82-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="f1e82-106">[in] `mdManifestResource` Token reprezentujący zasób, dla którego należy pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1e82-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="f1e82-107">[out] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="f1e82-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f1e82-108">[in] Rozmiar w szerokie znaki z `szName`.</span><span class="sxs-lookup"><span data-stu-id="f1e82-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f1e82-109">[out] Wskaźnik do liczby szerokie znaki rzeczywistego zwrotu w `szName`.</span><span class="sxs-lookup"><span data-stu-id="f1e82-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="f1e82-110">[out] Wskaźnik do `mdFile` tokenu lub `mdAssemblyRef` token reprezentujący pliku lub zestawu, odpowiednio, który zawiera zasób.</span><span class="sxs-lookup"><span data-stu-id="f1e82-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="f1e82-111">[out] Wskaźnik do wartości, który określa przesunięcie na początku tego zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="f1e82-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="f1e82-112">[out] Wskaźnik flagi opisujące metadanych dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="f1e82-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="f1e82-113">Wartość flagi składa się z co najmniej jeden [cormanifestresourceflags —](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="f1e82-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e82-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1e82-114">Requirements</span></span>  
 <span data-ttu-id="f1e82-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1e82-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1e82-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f1e82-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1e82-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1e82-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1e82-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e82-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e82-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1e82-119">See also</span></span>

- [<span data-ttu-id="f1e82-120">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1e82-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
