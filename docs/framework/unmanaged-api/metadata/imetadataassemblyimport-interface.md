---
title: "IMetaDataAssemblyImport — Interfejs"
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
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 992b588d16bc221f6b72044da40d09fbb6894511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="8c31a-102">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8c31a-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="8c31a-103">Udostępnia metody dostępu i sprawdź zawartość manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="8c31a-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c31a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8c31a-104">Methods</span></span>  
  
|<span data-ttu-id="8c31a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-105">Method</span></span>|<span data-ttu-id="8c31a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8c31a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c31a-107">CloseEnum, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="8c31a-108">Zwalnia dojścia do określonego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8c31a-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="8c31a-109">EnumAssemblyRefs, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="8c31a-110">Pobiera wskaźnika interfejsu, aby moduł wyliczający, który zawiera `mdAssemblyRef` tokeny zestawów odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c31a-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8c31a-111">EnumExportedTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="8c31a-112">Pobiera wskaźnika interfejsu, aby moduł wyliczający, który zawiera `mdExportedType` tokeny typów COM odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c31a-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8c31a-113">EnumFiles, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="8c31a-114">Pobiera wskaźnika interfejsu, aby moduł wyliczający, który zawiera `mdFile` tokeny plików odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c31a-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8c31a-115">EnumManifestResources, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="8c31a-116">Pobiera wskaźnika interfejsu, aby moduł wyliczający, który zawiera `mdManifestResource` tokenów zasobów odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c31a-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8c31a-117">FindAssembliesByName, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="8c31a-118">Pobiera tablicę `mdAssemblyRef` tokeny dla zestawów o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8c31a-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="8c31a-119">FindExportedTypeByName, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="8c31a-120">Pobiera `mdExportedType` tokenu dla typu modelu COM o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8c31a-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="8c31a-121">FindManifestResourceByName, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="8c31a-122">Pobiera `mdManifestResource` tokenu dla zasobu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8c31a-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="8c31a-123">GetAssemblyFromScope, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="8c31a-124">Pobiera token dla zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c31a-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8c31a-125">GetAssemblyProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="8c31a-126">Pobiera ustawienia właściwości określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8c31a-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="8c31a-127">GetAssemblyRefProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="8c31a-128">Pobiera ustawienia właściwości określonego `mdAssemblyRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="8c31a-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="8c31a-129">GetExportedTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="8c31a-130">Pobiera ustawienia właściwości określonego typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8c31a-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="8c31a-131">GetFileProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="8c31a-132">Pobiera ustawienia właściwości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="8c31a-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="8c31a-133">GetManifestResourceProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8c31a-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="8c31a-134">Pobiera ustawienia właściwości określonego zasobu manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c31a-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c31a-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c31a-135">Requirements</span></span>  
 <span data-ttu-id="8c31a-136">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c31a-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c31a-137">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8c31a-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c31a-138">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c31a-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c31a-139">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c31a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c31a-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c31a-140">See Also</span></span>  
 [<span data-ttu-id="8c31a-141">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="8c31a-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="8c31a-142">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c31a-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
