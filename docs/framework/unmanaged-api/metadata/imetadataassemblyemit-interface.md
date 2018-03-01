---
title: "IMetaDataAssemblyEmit — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6a7e4bd68bfd985b8902ae3b2340773ca77eee10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="e2fff-102">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e2fff-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="e2fff-103">Udostępnia metody, które obsługują modelu własny opis używany przez środowisko uruchomieniowe języka wspólnego do rozwiązania i użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="e2fff-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2fff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2fff-104">Methods</span></span>  
  
|<span data-ttu-id="e2fff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-105">Method</span></span>|<span data-ttu-id="e2fff-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e2fff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2fff-107">DefineAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="e2fff-108">Strukturę danych zestaw zawierający metadane dla określonego zestawu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="e2fff-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="e2fff-109">DefineAssemblyRef, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="e2fff-110">Tworzy `AssemblyRef` struktury zawierającej metadanych dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="e2fff-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="e2fff-111">DefineExportedType, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="e2fff-112">Tworzy `ExportedType` struktury zawierający metadane dla określonej wyeksportowanego typu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="e2fff-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="e2fff-113">DefineFile, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="e2fff-114">Tworzy `File` struktury metadane zawierające metadanych dla zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="e2fff-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="e2fff-115">DefineManifestResource, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="e2fff-116">Tworzy `ManifestResource` struktury metadane zawierające dla określonego zasobu manifestu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="e2fff-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="e2fff-117">SetAssemblyProps, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="e2fff-118">Modyfikuje określony `Assembly` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="e2fff-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="e2fff-119">SetAssemblyRefProps, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="e2fff-120">Modyfikuje określony `AssemblyRef` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="e2fff-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="e2fff-121">SetExportedTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="e2fff-122">Modyfikuje określony `ExportedType` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="e2fff-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="e2fff-123">SetFileProps, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="e2fff-124">Modyfikuje określony `File` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="e2fff-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="e2fff-125">SetManifestResourceProps, metoda</span><span class="sxs-lookup"><span data-stu-id="e2fff-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="e2fff-126">Modyfikuje określony `ManifestResource` struktura metadanych.</span><span class="sxs-lookup"><span data-stu-id="e2fff-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2fff-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2fff-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2fff-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2fff-128">Requirements</span></span>  
 <span data-ttu-id="e2fff-129">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2fff-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2fff-130">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e2fff-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2fff-131">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e2fff-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2fff-132">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2fff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2fff-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2fff-133">See Also</span></span>  
 [<span data-ttu-id="e2fff-134">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="e2fff-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="e2fff-135">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2fff-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
