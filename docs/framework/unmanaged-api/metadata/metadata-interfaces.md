---
title: Interfejsy metadanych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4672cb813cec4a127f7888a2273eb26c3f34c3d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431591"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="7b2b9-102">Interfejsy metadanych</span><span class="sxs-lookup"><span data-stu-id="7b2b9-102">Metadata Interfaces</span></span>
<span data-ttu-id="7b2b9-103">W tej sekcji opisano niezarządzane interfejsy, które zapewniają dostęp do metadanych uwidocznionych przez typy .NET Framework, metody, pola itd.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b2b9-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7b2b9-104">In This Section</span></span>  
 [<span data-ttu-id="7b2b9-105">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="7b2b9-106">Zapewnia metody dynamicznego kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="7b2b9-107">IHostFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="7b2b9-108">Zapewnia metodę dla hosta czasu wykonywania, aby oznaczyć tokeny metadanych do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="7b2b9-109">IMapToken, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="7b2b9-110">Oferuje możliwości mapowania między zaimportowanymi i emitowanymi sygnaturami metadanych.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="7b2b9-111">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="7b2b9-112">Dostarcza metody, które obsługują model z własnymi opisami używany przez środowisko uruchomieniowe języka wspólnego (CLR) do rozwiązywania i korzystania z zasobów.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="7b2b9-113">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="7b2b9-114">Zapewnia metody umożliwiające dostęp i sprawdzanie zawartości manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="7b2b9-115">IMetaDataConverter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="7b2b9-116">Zapewnia metody mapowania bibliotek typów na ich sygnatury metadanych oraz do konwersji między nimi.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="7b2b9-117">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="7b2b9-118">`IMetaDataDispenser` jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="7b2b9-119">Zamiast nich należy używać słów kluczowych `IMetaDataDispenserEx`.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="7b2b9-120">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="7b2b9-121">Dostarcza metody, które mapują obszary pamięci do tworzenia lub modyfikowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="7b2b9-122">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="7b2b9-123">Zapewnia metody tworzenia, modyfikowania i przechowywania metadanych dotyczących zestawu w aktualnie zdefiniowanym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="7b2b9-124">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="7b2b9-125">Zapewnia metody definiowania i modyfikowania sygnatur metadanych metod i konstruktorów z parametrami typu <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="7b2b9-126">IMetaDataError, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="7b2b9-127">Zapewnia mechanizm wywołania zwrotnego do raportowania błędów podczas rozpoznawania podpisu metadanych dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="7b2b9-128">IMetaDataFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="7b2b9-129">Zapewnia metody oznaczania i filtrowania tokenów metadanych, aby uniknąć powtarzających się akcji, które zostały już wykonane.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="7b2b9-130">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="7b2b9-131">Zapewnia metody importowania typów z innych zestawów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="7b2b9-132">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="7b2b9-133">Rozszerza `IMetaDataImport`, aby zapewnić możliwość pracy z typami ogólnymi.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="7b2b9-134">IMetaDataInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="7b2b9-135">Zapewnia metodę, która pobiera informacje o mapowaniu metadanych z pliku na dysku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="7b2b9-136">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="7b2b9-137">Zapewnia metody przechowywania i pobierania informacji o metadanych w tabelach.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="7b2b9-138">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="7b2b9-139">Rozszerza `IMetaDataTables`, aby uwzględnić metody pracy z strumieniami metadanych.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="7b2b9-140">IMetaDataValidate, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b2b9-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="7b2b9-141">Zapewnia metody do użycia w celu walidacji sygnatur metadanych.</span><span class="sxs-lookup"><span data-stu-id="7b2b9-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7b2b9-142">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7b2b9-142">Related Sections</span></span>  
 [<span data-ttu-id="7b2b9-143">Statyczne funkcje globalne metadanych</span><span class="sxs-lookup"><span data-stu-id="7b2b9-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="7b2b9-144">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="7b2b9-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="7b2b9-145">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="7b2b9-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="7b2b9-146">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="7b2b9-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
