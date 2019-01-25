---
title: IMetaDataAssemblyImport — Interfejs
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f213bcb9f87c34d23b53c2016bd841aae7c7194
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540285"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="8bbc2-102">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8bbc2-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="8bbc2-103">Udostępnia metody dostępu i sprawdź zawartość w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8bbc2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8bbc2-104">Methods</span></span>  
  
|<span data-ttu-id="8bbc2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-105">Method</span></span>|<span data-ttu-id="8bbc2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8bbc2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8bbc2-107">CloseEnum, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="8bbc2-108">Zwalnia dojścia do określonego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="8bbc2-109">EnumAssemblyRefs, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="8bbc2-110">Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdAssemblyRef` tokenów zestawów odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8bbc2-111">EnumExportedTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="8bbc2-112">Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdExportedType` tokenów typów modelu COM, który odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8bbc2-113">EnumFiles, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="8bbc2-114">Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdFile` tokeny plików odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8bbc2-115">EnumManifestResources, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="8bbc2-116">Pobiera moduł wyliczający, który zawiera wskaźnik interfejsu `mdManifestResource` tokenów zasobów odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8bbc2-117">FindAssembliesByName, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="8bbc2-118">Pobiera tablicę elementów `mdAssemblyRef` tokenów dla zespołów o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="8bbc2-119">FindExportedTypeByName, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="8bbc2-120">Pobiera `mdExportedType` tokenu dla typu COM o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="8bbc2-121">FindManifestResourceByName, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="8bbc2-122">Pobiera `mdManifestResource` tokenu dla zasobu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="8bbc2-123">GetAssemblyFromScope, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="8bbc2-124">Pobiera token dla zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="8bbc2-125">GetAssemblyProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="8bbc2-126">Pobiera ustawienia właściwości określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="8bbc2-127">GetAssemblyRefProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="8bbc2-128">Pobiera ustawienia właściwości określonego `mdAssemblyRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="8bbc2-129">GetExportedTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="8bbc2-130">Pobiera ustawienia właściwości określonego typu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="8bbc2-131">GetFileProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="8bbc2-132">Pobiera ustawienia właściwości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="8bbc2-133">GetManifestResourceProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8bbc2-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="8bbc2-134">Pobiera ustawienia właściwości określonego zasobu manifestu.</span><span class="sxs-lookup"><span data-stu-id="8bbc2-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bbc2-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bbc2-135">Requirements</span></span>  
 <span data-ttu-id="8bbc2-136">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bbc2-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bbc2-137">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8bbc2-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bbc2-138">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8bbc2-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bbc2-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bbc2-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bbc2-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bbc2-140">See also</span></span>
- [<span data-ttu-id="8bbc2-141">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="8bbc2-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="8bbc2-142">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="8bbc2-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
