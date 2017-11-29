---
title: "IMetaDataAssemblyImport::FindManifestResourceByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492f8a50c421df56d1b2f79d15d86ef3251b401e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="2c2f4-102">IMetaDataAssemblyImport::FindManifestResourceByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c2f4-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="2c2f4-103">Pobiera wskaźnik do zasobu manifestu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2c2f4-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c2f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c2f4-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c2f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c2f4-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="2c2f4-106">[in] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="2c2f4-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="2c2f4-107">[out] Tablica używany do przechowywania `mdManifestResource` tokenów metadanych, z których każdy reprezentuje zasobu manifestu.</span><span class="sxs-lookup"><span data-stu-id="2c2f4-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c2f4-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c2f4-108">Remarks</span></span>  
 <span data-ttu-id="2c2f4-109">`FindManifestResourceByName` Metoda używa standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="2c2f4-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c2f4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c2f4-110">Requirements</span></span>  
 <span data-ttu-id="2c2f4-111">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c2f4-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c2f4-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2c2f4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c2f4-113">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c2f4-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c2f4-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c2f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2f4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c2f4-115">See Also</span></span>  
 [<span data-ttu-id="2c2f4-116">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="2c2f4-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="2c2f4-117">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2c2f4-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
