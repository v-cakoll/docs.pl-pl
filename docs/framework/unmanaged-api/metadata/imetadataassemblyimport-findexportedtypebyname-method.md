---
title: IMetaDataAssemblyImport::FindExportedTypeByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7575659441b2eae37365c10050bca53e0cfdef6f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473919"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="5e1dc-102">IMetaDataAssemblyImport::FindExportedTypeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e1dc-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="5e1dc-103">Pobiera wskaźnik do typu wyeksportowanego, biorąc pod uwagę jego nazwę i typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e1dc-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e1dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e1dc-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="5e1dc-106">[in] Nazwa typu wyeksportowanego.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="5e1dc-107">[in] Token metadanych dla otaczającej klasy wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="5e1dc-108">Ta wartość jest `mdExportedTypeNil` w przypadku eksportu żądany typ nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="5e1dc-109">[out] Wskaźnik do `mdExportedType` token, który reprezentuje typ eksportowany.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e1dc-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e1dc-110">Remarks</span></span>  
 <span data-ttu-id="5e1dc-111">`FindExportedTypeByName` Metoda wykorzystuje standardowe reguły stosowane przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="5e1dc-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e1dc-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e1dc-112">Requirements</span></span>  
 <span data-ttu-id="5e1dc-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e1dc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e1dc-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5e1dc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e1dc-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e1dc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e1dc-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e1dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1dc-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e1dc-117">See also</span></span>
- [<span data-ttu-id="5e1dc-118">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e1dc-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="5e1dc-119">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5e1dc-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
