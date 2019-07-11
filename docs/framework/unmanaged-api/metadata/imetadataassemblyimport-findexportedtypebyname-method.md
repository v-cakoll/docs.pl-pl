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
ms.openlocfilehash: 8a70c041bc17f58a5e17877dd2e1f2aa2944e689
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777923"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="e32db-102">IMetaDataAssemblyImport::FindExportedTypeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="e32db-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="e32db-103">Pobiera wskaźnik do typu wyeksportowanego, biorąc pod uwagę jego nazwę i typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="e32db-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e32db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e32db-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e32db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e32db-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e32db-106">[in] Nazwa typu wyeksportowanego.</span><span class="sxs-lookup"><span data-stu-id="e32db-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="e32db-107">[in] Token metadanych dla otaczającej klasy wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="e32db-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="e32db-108">Ta wartość jest `mdExportedTypeNil` w przypadku eksportu żądany typ nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="e32db-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="e32db-109">[out] Wskaźnik do `mdExportedType` token, który reprezentuje typ eksportowany.</span><span class="sxs-lookup"><span data-stu-id="e32db-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e32db-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e32db-110">Remarks</span></span>  
 <span data-ttu-id="e32db-111">`FindExportedTypeByName` Metoda wykorzystuje standardowe reguły stosowane przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="e32db-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e32db-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e32db-112">Requirements</span></span>  
 <span data-ttu-id="e32db-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e32db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e32db-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e32db-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e32db-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e32db-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e32db-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e32db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32db-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e32db-117">See also</span></span>

- [<span data-ttu-id="e32db-118">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="e32db-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e32db-119">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e32db-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
