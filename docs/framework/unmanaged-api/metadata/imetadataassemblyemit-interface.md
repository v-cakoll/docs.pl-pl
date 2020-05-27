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
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008121"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="46d52-102">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="46d52-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="46d52-103">Dostarcza metody, które obsługują model z własnymi opisami używany przez środowisko uruchomieniowe języka wspólnego do rozwiązywania i korzystania z zasobów.</span><span class="sxs-lookup"><span data-stu-id="46d52-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46d52-104">Metody</span><span class="sxs-lookup"><span data-stu-id="46d52-104">Methods</span></span>  
  
|<span data-ttu-id="46d52-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-105">Method</span></span>|<span data-ttu-id="46d52-106">Opis</span><span class="sxs-lookup"><span data-stu-id="46d52-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46d52-107">DefineAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="46d52-108">Tworzy strukturę danych zestawu zawierającą metadane dla określonego zestawu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="46d52-109">DefineAssemblyRef — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="46d52-110">Tworzy `AssemblyRef` strukturę zawierającą metadane zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="46d52-111">DefineExportedType — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="46d52-112">Tworzy `ExportedType` strukturę zawierającą metadane dla określonego typu wyeksportowanego i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="46d52-113">DefineFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="46d52-114">Tworzy `File` strukturę metadanych zawierającą metadane zestawu, do którego odwołuje się ten zestaw, i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="46d52-115">DefineManifestResource — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="46d52-116">Tworzy `ManifestResource` strukturę zawierającą metadane dla określonego zasobu manifestu i zwraca skojarzony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="46d52-117">SetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="46d52-118">Modyfikuje określoną `Assembly` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="46d52-119">SetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="46d52-120">Modyfikuje określoną `AssemblyRef` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="46d52-121">SetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="46d52-122">Modyfikuje określoną `ExportedType` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="46d52-123">SetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="46d52-124">Modyfikuje określoną `File` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="46d52-125">SetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="46d52-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="46d52-126">Modyfikuje określoną `ManifestResource` strukturę metadanych.</span><span class="sxs-lookup"><span data-stu-id="46d52-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46d52-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46d52-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46d52-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46d52-128">Requirements</span></span>  
 <span data-ttu-id="46d52-129">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46d52-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d52-130">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="46d52-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46d52-131">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46d52-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46d52-132">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d52-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d52-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46d52-133">See also</span></span>

- [<span data-ttu-id="46d52-134">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="46d52-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="46d52-135">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="46d52-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
