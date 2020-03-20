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
ms.openlocfilehash: ae9097725aecd21e910e49a78d81951df39e9b2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177776"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="ecf2c-102">IMetaDataAssemblyImport::FindManifestResourceByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecf2c-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="ecf2c-103">Pobiera wskaźnik do zasobu manifestu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ecf2c-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf2c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecf2c-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="ecf2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecf2c-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ecf2c-106">[w] Nazwa zasobu.</span><span class="sxs-lookup"><span data-stu-id="ecf2c-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="ecf2c-107">[na zewnątrz] Tablica używana do `mdManifestResource` przechowywania tokenów metadanych, z których każdy reprezentuje zasób manifestu.</span><span class="sxs-lookup"><span data-stu-id="ecf2c-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecf2c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecf2c-108">Remarks</span></span>  
 <span data-ttu-id="ecf2c-109">Metoda `FindManifestResourceByName` używa standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="ecf2c-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecf2c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecf2c-110">Requirements</span></span>  
 <span data-ttu-id="ecf2c-111">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecf2c-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecf2c-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ecf2c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecf2c-113">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecf2c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecf2c-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecf2c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf2c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecf2c-115">See also</span></span>

- [<span data-ttu-id="ecf2c-116">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ecf2c-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="ecf2c-117">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ecf2c-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
