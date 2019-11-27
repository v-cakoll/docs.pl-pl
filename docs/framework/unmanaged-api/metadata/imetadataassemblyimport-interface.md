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
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436307"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="3ad90-102">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3ad90-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="3ad90-103">Zapewnia metody umożliwiające dostęp i sprawdzanie zawartości manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="3ad90-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ad90-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3ad90-104">Methods</span></span>  
  
|<span data-ttu-id="3ad90-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-105">Method</span></span>|<span data-ttu-id="3ad90-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3ad90-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ad90-107">CloseEnum, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="3ad90-108">Zwalnia dojście do określonego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="3ad90-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="3ad90-109">EnumAssemblyRefs, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="3ad90-110">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdAssemblyRef` tokeny zestawów, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="3ad90-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3ad90-111">EnumExportedTypes, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="3ad90-112">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdExportedType` tokeny typów COM, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="3ad90-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3ad90-113">EnumFiles, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="3ad90-114">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdFile` tokeny plików, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="3ad90-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3ad90-115">EnumManifestResources, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="3ad90-116">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdManifestResource` tokeny zasobów, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="3ad90-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3ad90-117">FindAssembliesByName, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="3ad90-118">Pobiera tablicę `mdAssemblyRef` tokenów dla zestawów o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3ad90-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="3ad90-119">FindExportedTypeByName, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="3ad90-120">Pobiera token `mdExportedType` dla typu COM o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3ad90-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="3ad90-121">FindManifestResourceByName, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="3ad90-122">Pobiera token `mdManifestResource` dla zasobu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="3ad90-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="3ad90-123">GetAssemblyFromScope, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="3ad90-124">Pobiera token dla zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="3ad90-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="3ad90-125">GetAssemblyProps, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="3ad90-126">Pobiera ustawienia właściwości określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3ad90-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="3ad90-127">GetAssemblyRefProps, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="3ad90-128">Pobiera ustawienia właściwości określonego tokenu `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="3ad90-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="3ad90-129">GetExportedTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="3ad90-130">Pobiera ustawienia właściwości określonego typu COM.</span><span class="sxs-lookup"><span data-stu-id="3ad90-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="3ad90-131">GetFileProps, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="3ad90-132">Pobiera ustawienia właściwości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="3ad90-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="3ad90-133">GetManifestResourceProps, metoda</span><span class="sxs-lookup"><span data-stu-id="3ad90-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="3ad90-134">Pobiera ustawienia właściwości określonego zasobu manifestu.</span><span class="sxs-lookup"><span data-stu-id="3ad90-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ad90-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ad90-135">Requirements</span></span>  
 <span data-ttu-id="3ad90-136">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ad90-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ad90-137">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3ad90-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ad90-138">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3ad90-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ad90-139">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ad90-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ad90-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ad90-140">See also</span></span>

- [<span data-ttu-id="3ad90-141">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="3ad90-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="3ad90-142">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ad90-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
