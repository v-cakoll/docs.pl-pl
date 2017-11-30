---
title: Interfejsy metadanych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 638727dae1f0f32e5c92c0da7513719bd11ae8d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-interfaces"></a><span data-ttu-id="b2962-102">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="b2962-102">Metadata Interfaces</span></span>
<span data-ttu-id="b2962-103">W tej sekcji opisano niezarządzane interfejsy, które umożliwiają dostęp do metadanych udostępnianych przez typy .NET Framework, metody, pól i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b2962-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2962-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b2962-104">In This Section</span></span>  
 [<span data-ttu-id="b2962-105">ICeeGen — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="b2962-106">Udostępnia metody dla kompilacji dynamicznej kodu.</span><span class="sxs-lookup"><span data-stu-id="b2962-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="b2962-107">IHostFilter — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="b2962-108">Zapewnia metodę host czasu wykonywania można oznaczyć tokenów metadanych do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b2962-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="b2962-109">IMapToken — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="b2962-110">Zapewnia możliwości mapowania między zaimportowane i wysyłanego podpisów metadanych.</span><span class="sxs-lookup"><span data-stu-id="b2962-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="b2962-111">IMetaDataAssemblyEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="b2962-112">Udostępnia metody, które obsługują modelu własny opis używany przez środowisko uruchomieniowe języka wspólnego (CLR) do rozwiązania i użycie zasobów.</span><span class="sxs-lookup"><span data-stu-id="b2962-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="b2962-113">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="b2962-114">Udostępnia metody dostępu i sprawdź zawartość manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2962-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="b2962-115">IMetaDataConverter — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="b2962-116">Udostępnia metody do mapowania biblioteki typów na ich podpisów metadanych i przekonwertować z jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="b2962-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="b2962-117">IMetaDataDispenser — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="b2962-118">`IMetaDataDispenser`jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="b2962-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="b2962-119">Zamiast nich należy używać słów kluczowych `IMetaDataDispenserEx`.</span><span class="sxs-lookup"><span data-stu-id="b2962-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="b2962-120">IMetaDataDispenserEx — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="b2962-121">Udostępnia metody, które mapują obszary pamięci dla tworzenia lub modyfikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="b2962-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="b2962-122">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="b2962-123">Udostępnia metody do tworzenia, modyfikowania i przechowywane metadane dotyczące zestawu w aktualnie określonego zakresu.</span><span class="sxs-lookup"><span data-stu-id="b2962-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="b2962-124">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="b2962-125">Udostępnia metody służące do definiowania i modyfikowania sygnatur metadanych z parametrami typu metody i konstruktory <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2962-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="b2962-126">IMetaDataError — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="b2962-127">Udostępnia mechanizm wywołania zwrotnego dla usługi raportowania błędów podczas rozpoznawania podpisu metadanych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2962-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="b2962-128">IMetaDataFilter — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="b2962-129">Udostępnia metody dla oznaczenie i Filtrowanie tokenów metadanych, aby uniknąć powtarzania działania, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="b2962-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="b2962-130">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="b2962-131">Udostępnia metody do importowania i manipulowanie typów od innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="b2962-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="b2962-132">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="b2962-133">Rozszerza `IMetaDataImport` możliwości pracy z typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="b2962-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="b2962-134">IMetaDataInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="b2962-135">Udostępnia metody, która pobiera informacje o mapowaniu metadanych z pliku na dysku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="b2962-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="b2962-136">IMetaDataTables — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="b2962-137">Udostępnia metody przechowywania i pobierania informacji o metadanych w tabelach.</span><span class="sxs-lookup"><span data-stu-id="b2962-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="b2962-138">IMetaDataTables2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="b2962-139">Rozszerza `IMetaDataTables` uwzględnienie metody pracy ze strumieni metadanych.</span><span class="sxs-lookup"><span data-stu-id="b2962-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="b2962-140">IMetaDataValidate — interfejs</span><span class="sxs-lookup"><span data-stu-id="b2962-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="b2962-141">Udostępnia metody do użycia w celu weryfikacji sygnatury metadanych.</span><span class="sxs-lookup"><span data-stu-id="b2962-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b2962-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b2962-142">Related Sections</span></span>  
 [<span data-ttu-id="b2962-143">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="b2962-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="b2962-144">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="b2962-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="b2962-145">Metadane struktury</span><span class="sxs-lookup"><span data-stu-id="b2962-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="b2962-146">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="b2962-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
