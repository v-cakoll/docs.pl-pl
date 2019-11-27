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
ms.openlocfilehash: 6b36d63101c1e9550a979d858764e9052cf45792
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447931"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="9c818-102">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9c818-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="9c818-103">Dostarcza metody, które obsługują model z własnymi opisami używany przez środowisko uruchomieniowe języka wspólnego do rozwiązywania i korzystania z zasobów.</span><span class="sxs-lookup"><span data-stu-id="9c818-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c818-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9c818-104">Methods</span></span>  
  
|<span data-ttu-id="9c818-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-105">Method</span></span>|<span data-ttu-id="9c818-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9c818-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c818-107">DefineAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="9c818-108">Tworzy strukturę danych zestawu zawierającą metadane dla określonego zestawu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9c818-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="9c818-109">DefineAssemblyRef, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="9c818-110">Tworzy strukturę `AssemblyRef` zawierającą metadane zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9c818-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="9c818-111">DefineExportedType, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="9c818-112">Tworzy strukturę `ExportedType` zawierającą metadane dla określonego typu wyeksportowanego i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9c818-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="9c818-113">DefineFile, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="9c818-114">Tworzy `File` strukturę metadanych zawierającą metadane zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9c818-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="9c818-115">DefineManifestResource, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="9c818-116">Tworzy strukturę `ManifestResource` zawierającą metadane dla określonego zasobu manifestu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9c818-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="9c818-117">SetAssemblyProps, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="9c818-118">Modyfikuje określoną strukturę metadanych `Assembly`.</span><span class="sxs-lookup"><span data-stu-id="9c818-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="9c818-119">SetAssemblyRefProps, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="9c818-120">Modyfikuje określoną strukturę metadanych `AssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="9c818-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="9c818-121">SetExportedTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="9c818-122">Modyfikuje określoną strukturę metadanych `ExportedType`.</span><span class="sxs-lookup"><span data-stu-id="9c818-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="9c818-123">SetFileProps, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="9c818-124">Modyfikuje określoną strukturę metadanych `File`.</span><span class="sxs-lookup"><span data-stu-id="9c818-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="9c818-125">SetManifestResourceProps, metoda</span><span class="sxs-lookup"><span data-stu-id="9c818-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="9c818-126">Modyfikuje określoną strukturę metadanych `ManifestResource`.</span><span class="sxs-lookup"><span data-stu-id="9c818-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c818-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c818-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c818-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c818-128">Requirements</span></span>  
 <span data-ttu-id="9c818-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c818-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c818-130">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9c818-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c818-131">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9c818-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c818-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c818-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c818-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c818-133">See also</span></span>

- [<span data-ttu-id="9c818-134">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="9c818-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="9c818-135">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="9c818-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
