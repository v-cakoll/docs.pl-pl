---
title: "IMetaDataAssemblyImport::FindExportedTypeByName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindExportedTypeByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7ef0e09cb5a44e612e545fc4ee7278c2d128174
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="b0f84-102">IMetaDataAssemblyImport::FindExportedTypeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0f84-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="b0f84-103">Pobiera wskaźnik do wyeksportowanego typu podanej nazwy i typ otaczający.</span><span class="sxs-lookup"><span data-stu-id="b0f84-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0f84-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0f84-104">Syntax</span></span>  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0f84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0f84-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b0f84-106">[in] Nazwa wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="b0f84-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="b0f84-107">[in] Token metadanych dla wyeksportowanego typu klasy otaczającej.</span><span class="sxs-lookup"><span data-stu-id="b0f84-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="b0f84-108">Ta wartość jest `mdExportedTypeNil` Jeśli wyeksportowany żądany typ nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="b0f84-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="b0f84-109">[out] Wskaźnik do `mdExportedType` token reprezentujący wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="b0f84-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0f84-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0f84-110">Remarks</span></span>  
 <span data-ttu-id="b0f84-111">`FindExportedTypeByName` Metoda używa standardowych zasad stosowanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="b0f84-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0f84-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0f84-112">Requirements</span></span>  
 <span data-ttu-id="b0f84-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0f84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0f84-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b0f84-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0f84-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0f84-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0f84-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0f84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f84-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0f84-117">See Also</span></span>  
 [<span data-ttu-id="b0f84-118">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="b0f84-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="b0f84-119">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b0f84-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
