---
title: IMetaDataAssemblyImport::FindManifestResourceByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf61da362251577acadb83915404eba7508b3099
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141573"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="80921-102">IMetaDataAssemblyImport::FindManifestResourceByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="80921-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="80921-103">Pobiera wskaźnik do zasobu manifestu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="80921-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80921-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80921-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="80921-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80921-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="80921-106">[in] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="80921-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="80921-107">[out] Tablica do przechowywania `mdManifestResource` tokeny metadanych, z których każdy reprezentuje zasobu manifestu.</span><span class="sxs-lookup"><span data-stu-id="80921-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80921-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80921-108">Remarks</span></span>  
 <span data-ttu-id="80921-109">`FindManifestResourceByName` Metoda wykorzystuje standardowe reguły stosowane przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="80921-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80921-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80921-110">Requirements</span></span>  
 <span data-ttu-id="80921-111">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80921-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80921-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="80921-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80921-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80921-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="80921-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="80921-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="80921-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80921-115">See also</span></span>

- [<span data-ttu-id="80921-116">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="80921-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="80921-117">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="80921-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
