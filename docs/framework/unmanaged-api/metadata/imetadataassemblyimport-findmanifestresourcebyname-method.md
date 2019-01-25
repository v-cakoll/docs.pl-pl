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
ms.openlocfilehash: b05c9a75bf870dd3b2316d2df7c50932b26894f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702746"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="e9a3a-102">IMetaDataAssemblyImport::FindManifestResourceByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9a3a-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="e9a3a-103">Pobiera wskaźnik do zasobu manifestu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="e9a3a-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9a3a-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9a3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9a3a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e9a3a-106">[in] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="e9a3a-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="e9a3a-107">[out] Tablica do przechowywania `mdManifestResource` tokeny metadanych, z których każdy reprezentuje zasobu manifestu.</span><span class="sxs-lookup"><span data-stu-id="e9a3a-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9a3a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9a3a-108">Remarks</span></span>  
 <span data-ttu-id="e9a3a-109">`FindManifestResourceByName` Metoda wykorzystuje standardowe reguły stosowane przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="e9a3a-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a3a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9a3a-110">Requirements</span></span>  
 <span data-ttu-id="e9a3a-111">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9a3a-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a3a-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e9a3a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9a3a-113">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9a3a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9a3a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a3a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a3a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9a3a-115">See also</span></span>
- [<span data-ttu-id="e9a3a-116">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="e9a3a-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e9a3a-117">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e9a3a-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
