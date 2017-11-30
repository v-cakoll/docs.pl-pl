---
title: "IMetaDataAssemblyEmit — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit
helpviewer_keywords: IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af7a5fd5a564aa7366924f47b0c526aff7153521
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="6d47e-102">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6d47e-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="6d47e-103">Udostępnia metody, które obsługują modelu własny opis używany przez środowisko uruchomieniowe języka wspólnego do rozwiązania i użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="6d47e-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d47e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6d47e-104">Methods</span></span>  
  
|<span data-ttu-id="6d47e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-105">Method</span></span>|<span data-ttu-id="6d47e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6d47e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d47e-107">DefineAssembly — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="6d47e-108">Strukturę danych zestaw zawierający metadane dla określonego zestawu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="6d47e-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6d47e-109">DefineAssemblyRef — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="6d47e-110">Tworzy `AssemblyRef` struktury zawierającej metadanych dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="6d47e-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6d47e-111">DefineExportedType — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="6d47e-112">Tworzy `ExportedType` struktury zawierający metadane dla określonej wyeksportowanego typu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="6d47e-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6d47e-113">DefineFile — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="6d47e-114">Tworzy `File` struktury metadane zawierające metadanych dla zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="6d47e-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6d47e-115">DefineManifestResource — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="6d47e-116">Tworzy `ManifestResource` struktury metadane zawierające dla określonego zasobu manifestu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="6d47e-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6d47e-117">SetAssemblyProps — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="6d47e-118">Modyfikuje określony `Assembly` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="6d47e-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="6d47e-119">SetAssemblyRefProps — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="6d47e-120">Modyfikuje określony `AssemblyRef` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="6d47e-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="6d47e-121">SetExportedTypeProps — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="6d47e-122">Modyfikuje określony `ExportedType` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="6d47e-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="6d47e-123">SetFileProps — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="6d47e-124">Modyfikuje określony `File` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="6d47e-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="6d47e-125">SetManifestResourceProps — metoda</span><span class="sxs-lookup"><span data-stu-id="6d47e-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="6d47e-126">Modyfikuje określony `ManifestResource` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="6d47e-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d47e-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d47e-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d47e-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d47e-128">Requirements</span></span>  
 <span data-ttu-id="6d47e-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d47e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d47e-130">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d47e-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d47e-131">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d47e-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d47e-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d47e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d47e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d47e-133">See Also</span></span>  
 [<span data-ttu-id="6d47e-134">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="6d47e-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="6d47e-135">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="6d47e-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
