---
title: Interfejsy metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a704d531b1c49ffe653009e0e90f33b7a126e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-interfaces"></a><span data-ttu-id="7aa8d-102">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="7aa8d-102">Metadata Interfaces</span></span>
<span data-ttu-id="7aa8d-103">W tej sekcji opisano niezarządzane interfejsy, które umożliwiają dostęp do metadanych udostępnianych przez typy .NET Framework, metody, pól i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7aa8d-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7aa8d-104">In This Section</span></span>  
 [<span data-ttu-id="7aa8d-105">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="7aa8d-106">Udostępnia metody dla kompilacji dynamicznej kodu.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="7aa8d-107">IHostFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="7aa8d-108">Zapewnia metodę host czasu wykonywania można oznaczyć tokenów metadanych do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="7aa8d-109">IMapToken, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="7aa8d-110">Zapewnia możliwości mapowania między zaimportowane i wysyłanego podpisów metadanych.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="7aa8d-111">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="7aa8d-112">Udostępnia metody, które obsługują modelu własny opis używany przez środowisko uruchomieniowe języka wspólnego (CLR) do rozwiązania i użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="7aa8d-113">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="7aa8d-114">Udostępnia metody dostępu i sprawdź zawartość manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="7aa8d-115">IMetaDataConverter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="7aa8d-116">Udostępnia metody do mapowania biblioteki typów na ich podpisów metadanych i przekonwertować z jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="7aa8d-117">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="7aa8d-118">`IMetaDataDispenser` jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="7aa8d-119">Zamiast nich należy używać słów kluczowych `IMetaDataDispenserEx`.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="7aa8d-120">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="7aa8d-121">Udostępnia metody, które mapują obszary pamięci dla tworzenia lub modyfikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="7aa8d-122">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="7aa8d-123">Udostępnia metody do tworzenia, modyfikowania i przechowywane metadane dotyczące zestawu w aktualnie określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="7aa8d-124">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="7aa8d-125">Udostępnia metody służące do definiowania i modyfikowania sygnatur metadanych z parametrami typu metody i konstruktory <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="7aa8d-126">IMetaDataError, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="7aa8d-127">Udostępnia mechanizm wywołania zwrotnego dla usługi raportowania błędów podczas rozpoznawania podpisu metadanych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="7aa8d-128">IMetaDataFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="7aa8d-129">Udostępnia metody dla oznaczenie i Filtrowanie tokenów metadanych, aby uniknąć powtarzania działania, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="7aa8d-130">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="7aa8d-131">Udostępnia metody do importowania i manipulowanie typów od innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="7aa8d-132">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="7aa8d-133">Rozszerza `IMetaDataImport` możliwości pracy z typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="7aa8d-134">IMetaDataInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="7aa8d-135">Udostępnia metody, która pobiera informacje o mapowaniu metadanych z pliku na dysku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="7aa8d-136">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="7aa8d-137">Udostępnia metody przechowywania i pobierania informacji o metadanych w tabelach.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="7aa8d-138">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="7aa8d-139">Rozszerza `IMetaDataTables` uwzględnienie metody pracy ze strumieni metadanych.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="7aa8d-140">IMetaDataValidate, interfejs</span><span class="sxs-lookup"><span data-stu-id="7aa8d-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="7aa8d-141">Udostępnia metody do użycia w celu weryfikacji sygnatury metadanych.</span><span class="sxs-lookup"><span data-stu-id="7aa8d-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7aa8d-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7aa8d-142">Related Sections</span></span>  
 [<span data-ttu-id="7aa8d-143">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="7aa8d-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="7aa8d-144">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="7aa8d-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="7aa8d-145">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="7aa8d-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="7aa8d-146">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="7aa8d-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
