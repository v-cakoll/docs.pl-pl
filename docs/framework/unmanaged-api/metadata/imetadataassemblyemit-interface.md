---
title: IMetaDataAssemblyEmit — Interfejs
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3a66ef090a205019493e099919739867e3936873
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081806"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="7dd59-102">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7dd59-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="7dd59-103">Udostępnia metody, które wspierają model własny opis używany przez środowisko uruchomieniowe języka wspólnego w rozwiązania i używanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="7dd59-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7dd59-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7dd59-104">Methods</span></span>  
  
|<span data-ttu-id="7dd59-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-105">Method</span></span>|<span data-ttu-id="7dd59-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7dd59-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7dd59-107">DefineAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="7dd59-108">Tworzy zestaw danych struktury zawierającej metadanych dla określonego zestawu i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="7dd59-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7dd59-109">DefineAssemblyRef, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="7dd59-110">Tworzy `AssemblyRef` struktury zawierający metadane dla zestawu, który odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="7dd59-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7dd59-111">DefineExportedType, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="7dd59-112">Tworzy `ExportedType` struktury zawierającej metadanych dla określonego wyeksportować typu, a następnie zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="7dd59-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7dd59-113">DefineFile, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="7dd59-114">Tworzy `File` struktury metadanych zawierający metadane zestawu odwołuje się ten zestaw i zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="7dd59-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7dd59-115">DefineManifestResource, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="7dd59-116">Tworzy `ManifestResource` struktury zawierającymi metadane dla określonego zasobu manifestu, a następnie zwraca token skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="7dd59-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="7dd59-117">SetAssemblyProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="7dd59-118">Modyfikuje określonego `Assembly` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="7dd59-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="7dd59-119">SetAssemblyRefProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="7dd59-120">Modyfikuje określonego `AssemblyRef` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="7dd59-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="7dd59-121">SetExportedTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="7dd59-122">Modyfikuje określonego `ExportedType` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="7dd59-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="7dd59-123">SetFileProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="7dd59-124">Modyfikuje określonego `File` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="7dd59-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="7dd59-125">SetManifestResourceProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7dd59-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="7dd59-126">Modyfikuje określonego `ManifestResource` struktury metadanych.</span><span class="sxs-lookup"><span data-stu-id="7dd59-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dd59-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7dd59-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd59-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7dd59-128">Requirements</span></span>  
 <span data-ttu-id="7dd59-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dd59-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd59-130">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7dd59-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dd59-131">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7dd59-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7dd59-132">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd59-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd59-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dd59-133">See also</span></span>

- [<span data-ttu-id="7dd59-134">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="7dd59-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="7dd59-135">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7dd59-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
