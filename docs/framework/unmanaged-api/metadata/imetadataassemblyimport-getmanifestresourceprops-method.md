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
ms.openlocfilehash: ba99d84686974b425bcdee0bbf4770e4843e1351
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081666"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="17352-102">IMetaDataAssemblyImport::GetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="17352-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="17352-103">Pobiera zestaw właściwości zasobu manifestu o podpisie określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="17352-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17352-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17352-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="17352-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="17352-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="17352-106">[in] `mdManifestResource` Token reprezentujący zasób, dla którego należy pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="17352-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="17352-107">[out] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="17352-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="17352-108">[in] Rozmiar w szerokie znaki z `szName`.</span><span class="sxs-lookup"><span data-stu-id="17352-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="17352-109">[out] Wskaźnik do liczby szerokie znaki rzeczywistego zwrotu w `szName`.</span><span class="sxs-lookup"><span data-stu-id="17352-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="17352-110">[out] Wskaźnik do `mdFile` tokenu lub `mdAssemblyRef` token reprezentujący pliku lub zestawu, odpowiednio, który zawiera zasób.</span><span class="sxs-lookup"><span data-stu-id="17352-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="17352-111">[out] Wskaźnik do wartości, który określa przesunięcie na początku tego zasobu w pliku.</span><span class="sxs-lookup"><span data-stu-id="17352-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="17352-112">[out] Wskaźnik flagi opisujące metadanych dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="17352-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="17352-113">Wartość flagi składa się z co najmniej jeden [cormanifestresourceflags —](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="17352-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17352-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="17352-114">Requirements</span></span>  
 <span data-ttu-id="17352-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17352-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17352-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="17352-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17352-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17352-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="17352-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="17352-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="17352-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17352-119">See also</span></span>

- [<span data-ttu-id="17352-120">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="17352-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
