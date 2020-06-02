---
title: Entity Data Model
description: Entity Data Model opisuje strukturę danych, niezależnie od jej przechowywanego formularza, który rozwiązuje wyzwania związane z przechowywaniem danych w wielu formularzach.
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: c98b1f4559ef297f8b11051940fd91f5f6fa06fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286743"
---
# <a name="entity-data-model"></a><span data-ttu-id="adbdb-103">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="adbdb-103">Entity Data Model</span></span>
<span data-ttu-id="adbdb-104">Entity Data Model (EDM) to zestaw koncepcji, które opisują strukturę danych, niezależnie od ich przechowywanego formularza.</span><span class="sxs-lookup"><span data-stu-id="adbdb-104">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="adbdb-105">Model EDM jest pożyczany z modelu Entity-Relationship opisanego przez Peterowi Chen w 1976, ale również kompiluje się w modelu relacji jednostki i rozszerza jego tradycyjne zastosowania.</span><span class="sxs-lookup"><span data-stu-id="adbdb-105">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="adbdb-106">Modelu EDM zaspokaja wyzwania wynikające z posiadania danych przechowywanych w wielu formularzach.</span><span class="sxs-lookup"><span data-stu-id="adbdb-106">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="adbdb-107">Rozważmy na przykład firmę, która przechowuje dane w relacyjnych bazach danych, plikach tekstowych, plikach XML, arkuszach kalkulacyjnych i raportach.</span><span class="sxs-lookup"><span data-stu-id="adbdb-107">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="adbdb-108">Zapewnia to znaczne wyzwania w zakresie modelowania danych, projektowania aplikacji i dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="adbdb-108">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="adbdb-109">Podczas projektowania aplikacji zorientowanej na dane, wyzwanie polega na napisaniu wydajnego i obsługiwanego kodu bez poświęcania wydajnego dostępu do danych, magazynowania i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="adbdb-109">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="adbdb-110">Gdy dane mają strukturę relacyjną, dostęp do danych, magazyn i skalowalność są bardzo wydajne, ale pisanie wydajnego i konserwowanego kodu jest trudniejsze.</span><span class="sxs-lookup"><span data-stu-id="adbdb-110">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="adbdb-111">W przypadku, gdy dane mają strukturę obiektów, te wady są odwrócone: pisanie wydajnego i obsługiwanego kodu jest kosztem wydajnego dostępu do danych, magazynowania i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="adbdb-111">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="adbdb-112">Nawet w przypadku, gdy można znaleźć odpowiednie saldo między nimi, nowe wyzwania powstają, gdy dane są przenoszone z jednej formy do innej.</span><span class="sxs-lookup"><span data-stu-id="adbdb-112">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="adbdb-113">Entity Data Model rozwiązuje te problemy, opisując strukturę danych w odniesieniu do jednostek i relacji, które są niezależne od schematu magazynu.</span><span class="sxs-lookup"><span data-stu-id="adbdb-113">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="adbdb-114">Dzięki temu przechowywanie danych nie jest istotne dla projektowania i opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adbdb-114">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="adbdb-115">I, ponieważ jednostki i relacje opisują strukturę danych, która jest używana w aplikacji (a nie w formie przechowywanej), można je rozwijać w miarę rozwoju aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adbdb-115">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="adbdb-116">A `conceptual model` jest określoną reprezentacją struktury danych jako jednostek i relacji i jest ogólnie zdefiniowana w języku specyficznym dla domeny (DSL), który implementuje koncepcje modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="adbdb-116">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="adbdb-117">Przykładem takiego języka specyficznego dla domeny jest [język w języku definicji schematu koncepcyjnego (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) .</span><span class="sxs-lookup"><span data-stu-id="adbdb-117">[Conceptual schema definition language (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) is an example of such a domain-specific language.</span></span> <span data-ttu-id="adbdb-118">Jednostki i relacje opisane w modelu koncepcyjnym można traktować jako abstrakcje obiektów i skojarzeń w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adbdb-118">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="adbdb-119">Pozwala to deweloperom skupić się na modelu koncepcyjnym bez obaw dla schematu magazynu i umożliwia im pisanie kodu z wydajnością i łatwość utrzymania.</span><span class="sxs-lookup"><span data-stu-id="adbdb-119">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="adbdb-120">Projektanci schematów magazynu mogą skupić się na wydajności dostępu do danych, magazynowania i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="adbdb-120">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="adbdb-121">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="adbdb-121">In This Section</span></span>  
 <span data-ttu-id="adbdb-122">Tematy w tej sekcji opisują koncepcje Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="adbdb-122">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="adbdb-123">Wszystkie DSL, które implementują modelu EDM, powinny zawierać Koncepcje opisane tutaj.</span><span class="sxs-lookup"><span data-stu-id="adbdb-123">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="adbdb-124">Należy pamiętać, że [ADO.NET Entity Framework](./ef/index.md) używa CSDL do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="adbdb-124">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="adbdb-125">Aby uzyskać więcej informacji, zobacz [Specyfikacja CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span><span class="sxs-lookup"><span data-stu-id="adbdb-125">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span>  
  
 [<span data-ttu-id="adbdb-126">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="adbdb-126">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="adbdb-127">Model danych jednostki: Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="adbdb-127">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="adbdb-128">Model danych jednostki: Typy danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="adbdb-128">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="adbdb-129">Model danych jednostki: Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="adbdb-129">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="adbdb-130">punkt końcowy skojarzenia</span><span class="sxs-lookup"><span data-stu-id="adbdb-130">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="adbdb-131">skojarzenie i liczebność</span><span class="sxs-lookup"><span data-stu-id="adbdb-131">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="adbdb-132">zestaw skojarzeń</span><span class="sxs-lookup"><span data-stu-id="adbdb-132">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="adbdb-133">punkt końcowy zestawu skojarzeń</span><span class="sxs-lookup"><span data-stu-id="adbdb-133">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="adbdb-134">typ skojarzenia</span><span class="sxs-lookup"><span data-stu-id="adbdb-134">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="adbdb-135">typ złożony</span><span class="sxs-lookup"><span data-stu-id="adbdb-135">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="adbdb-136">kontener jednostek</span><span class="sxs-lookup"><span data-stu-id="adbdb-136">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="adbdb-137">klucz jednostki</span><span class="sxs-lookup"><span data-stu-id="adbdb-137">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="adbdb-138">zestaw jednostek</span><span class="sxs-lookup"><span data-stu-id="adbdb-138">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="adbdb-139">typ jednostki</span><span class="sxs-lookup"><span data-stu-id="adbdb-139">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="adbdb-140">facet</span><span class="sxs-lookup"><span data-stu-id="adbdb-140">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="adbdb-141">właściwość klucza obcego</span><span class="sxs-lookup"><span data-stu-id="adbdb-141">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="adbdb-142">funkcja zadeklarowana modelu</span><span class="sxs-lookup"><span data-stu-id="adbdb-142">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="adbdb-143">funkcja zdefiniowana przez model</span><span class="sxs-lookup"><span data-stu-id="adbdb-143">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="adbdb-144">właściwość nawigacji</span><span class="sxs-lookup"><span data-stu-id="adbdb-144">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="adbdb-145">wartość</span><span class="sxs-lookup"><span data-stu-id="adbdb-145">property</span></span>](property.md)  
  
 [<span data-ttu-id="adbdb-146">ograniczenie integralności referencyjnej</span><span class="sxs-lookup"><span data-stu-id="adbdb-146">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="adbdb-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adbdb-147">See also</span></span>

- <span data-ttu-id="adbdb-148">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="adbdb-148">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="adbdb-149">[Plik. edmx — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="adbdb-149">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="adbdb-150">Specyfikacja CSDL</span><span class="sxs-lookup"><span data-stu-id="adbdb-150">CSDL Specification</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
