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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009018"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="03453-102">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03453-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="03453-103">Zapewnia metody umożliwiające dostęp i sprawdzanie zawartości manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="03453-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03453-104">Metody</span><span class="sxs-lookup"><span data-stu-id="03453-104">Methods</span></span>  
  
|<span data-ttu-id="03453-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-105">Method</span></span>|<span data-ttu-id="03453-106">Opis</span><span class="sxs-lookup"><span data-stu-id="03453-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03453-107">CloseEnum, metoda</span><span class="sxs-lookup"><span data-stu-id="03453-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="03453-108">Zwalnia dojście do określonego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="03453-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="03453-109">EnumAssemblyRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="03453-110">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdAssemblyRef` tokeny zestawów, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="03453-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="03453-111">EnumExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="03453-112">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdExportedType` tokeny typów com, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="03453-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="03453-113">EnumFiles — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="03453-114">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdFile` tokeny plików, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="03453-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="03453-115">EnumManifestResources — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="03453-116">Pobiera wskaźnik interfejsu do modułu wyliczającego, który zawiera `mdManifestResource` tokeny zasobów, do których odwołuje się zestaw w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="03453-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="03453-117">FindAssembliesByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="03453-118">Pobiera tablicę `mdAssemblyRef` tokenów dla zestawów o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="03453-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="03453-119">FindExportedTypeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="03453-120">Pobiera `mdExportedType` token dla typu com o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="03453-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="03453-121">FindManifestResourceByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="03453-122">Pobiera `mdManifestResource` token dla zasobu o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="03453-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="03453-123">GetAssemblyFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="03453-124">Pobiera token dla zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="03453-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="03453-125">GetAssemblyProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="03453-126">Pobiera ustawienia właściwości określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="03453-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="03453-127">GetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="03453-128">Pobiera ustawienia właściwości określonego `mdAssemblyRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="03453-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="03453-129">GetExportedTypeProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="03453-130">Pobiera ustawienia właściwości określonego typu COM.</span><span class="sxs-lookup"><span data-stu-id="03453-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="03453-131">GetFileProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="03453-132">Pobiera ustawienia właściwości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="03453-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="03453-133">GetManifestResourceProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="03453-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="03453-134">Pobiera ustawienia właściwości określonego zasobu manifestu.</span><span class="sxs-lookup"><span data-stu-id="03453-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03453-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03453-135">Requirements</span></span>  
 <span data-ttu-id="03453-136">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03453-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03453-137">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="03453-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03453-138">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03453-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03453-139">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03453-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03453-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03453-140">See also</span></span>

- [<span data-ttu-id="03453-141">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="03453-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="03453-142">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03453-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
