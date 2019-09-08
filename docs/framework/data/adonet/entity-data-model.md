---
title: Entity Data Model
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: 1742b04d0e3d8387e990d40d832e355dd15c4311
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783958"
---
# <a name="entity-data-model"></a><span data-ttu-id="28ae1-102">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="28ae1-102">Entity Data Model</span></span>
<span data-ttu-id="28ae1-103">Entity Data Model (EDM) to zestaw koncepcji, które opisują strukturę danych, niezależnie od ich przechowywanego formularza.</span><span class="sxs-lookup"><span data-stu-id="28ae1-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="28ae1-104">Model EDM jest pożyczany z modelu Entity-Relationship opisanego przez Peterowi Chen w 1976, ale również kompiluje się w modelu relacji jednostki i rozszerza jego tradycyjne zastosowania.</span><span class="sxs-lookup"><span data-stu-id="28ae1-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="28ae1-105">Modelu EDM zaspokaja wyzwania wynikające z posiadania danych przechowywanych w wielu formularzach.</span><span class="sxs-lookup"><span data-stu-id="28ae1-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="28ae1-106">Rozważmy na przykład firmę, która przechowuje dane w relacyjnych bazach danych, plikach tekstowych, plikach XML, arkuszach kalkulacyjnych i raportach.</span><span class="sxs-lookup"><span data-stu-id="28ae1-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="28ae1-107">Zapewnia to znaczne wyzwania w zakresie modelowania danych, projektowania aplikacji i dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="28ae1-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="28ae1-108">Podczas projektowania aplikacji zorientowanej na dane, wyzwanie polega na napisaniu wydajnego i obsługiwanego kodu bez poświęcania wydajnego dostępu do danych, magazynowania i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="28ae1-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="28ae1-109">Gdy dane mają strukturę relacyjną, dostęp do danych, magazyn i skalowalność są bardzo wydajne, ale pisanie wydajnego i konserwowanego kodu jest trudniejsze.</span><span class="sxs-lookup"><span data-stu-id="28ae1-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="28ae1-110">W przypadku, gdy dane mają strukturę obiektu, jego wady są odwrócone: Tworzenie wydajnego i obsługiwanego kodu jest kosztem wydajnego dostępu do danych, magazynowania i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="28ae1-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="28ae1-111">Nawet w przypadku, gdy można znaleźć odpowiednie saldo między nimi, nowe wyzwania powstają, gdy dane są przenoszone z jednej formy do innej.</span><span class="sxs-lookup"><span data-stu-id="28ae1-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="28ae1-112">Entity Data Model rozwiązuje te problemy, opisując strukturę danych w odniesieniu do jednostek i relacji, które są niezależne od schematu magazynu.</span><span class="sxs-lookup"><span data-stu-id="28ae1-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="28ae1-113">Dzięki temu przechowywanie danych nie jest istotne dla projektowania i opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28ae1-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="28ae1-114">I, ponieważ jednostki i relacje opisują strukturę danych, która jest używana w aplikacji (a nie w formie przechowywanej), można je rozwijać w miarę rozwoju aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28ae1-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="28ae1-115">A `conceptual model` jest określoną reprezentacją struktury danych jako jednostek i relacji i jest ogólnie zdefiniowana w języku specyficznym dla domeny (DSL), który implementuje koncepcje modelu EDM.</span><span class="sxs-lookup"><span data-stu-id="28ae1-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="28ae1-116">Przykładem takiego języka specyficznego dla domeny jest [język w języku definicji schematu koncepcyjnego (CSDL)](./ef/language-reference/csdl-specification.md) .</span><span class="sxs-lookup"><span data-stu-id="28ae1-116">[Conceptual schema definition language (CSDL)](./ef/language-reference/csdl-specification.md) is an example of such a domain-specific language.</span></span> <span data-ttu-id="28ae1-117">Jednostki i relacje opisane w modelu koncepcyjnym można traktować jako abstrakcje obiektów i skojarzeń w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28ae1-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="28ae1-118">Pozwala to deweloperom skupić się na modelu koncepcyjnym bez obaw dla schematu magazynu i umożliwia im pisanie kodu z wydajnością i łatwość utrzymania.</span><span class="sxs-lookup"><span data-stu-id="28ae1-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="28ae1-119">Projektanci schematów magazynu mogą skupić się na wydajności dostępu do danych, magazynowania i skalowalności.</span><span class="sxs-lookup"><span data-stu-id="28ae1-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28ae1-120">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="28ae1-120">In This Section</span></span>  
 <span data-ttu-id="28ae1-121">Tematy w tej sekcji opisują koncepcje Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="28ae1-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="28ae1-122">Wszystkie DSL, które implementują modelu EDM, powinny zawierać Koncepcje opisane tutaj.</span><span class="sxs-lookup"><span data-stu-id="28ae1-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="28ae1-123">Należy pamiętać, że [ADO.NET Entity Framework](./ef/index.md) używa CSDL do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="28ae1-123">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="28ae1-124">Aby uzyskać więcej informacji, zobacz [Specyfikacja CSDL](./ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="28ae1-124">For more information, see [CSDL Specification](./ef/language-reference/csdl-specification.md).</span></span>  
  
 [<span data-ttu-id="28ae1-125">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="28ae1-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="28ae1-126">Entity Data Model: Przestrzeni</span><span class="sxs-lookup"><span data-stu-id="28ae1-126">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="28ae1-127">Entity Data Model: Typy danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="28ae1-127">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="28ae1-128">Entity Data Model: Strukturze</span><span class="sxs-lookup"><span data-stu-id="28ae1-128">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="28ae1-129">punkt końcowy skojarzenia</span><span class="sxs-lookup"><span data-stu-id="28ae1-129">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="28ae1-130">skojarzenie i liczebność</span><span class="sxs-lookup"><span data-stu-id="28ae1-130">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="28ae1-131">zestaw skojarzeń</span><span class="sxs-lookup"><span data-stu-id="28ae1-131">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="28ae1-132">punkt końcowy zestawu skojarzeń</span><span class="sxs-lookup"><span data-stu-id="28ae1-132">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="28ae1-133">typ skojarzenia</span><span class="sxs-lookup"><span data-stu-id="28ae1-133">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="28ae1-134">typ złożony</span><span class="sxs-lookup"><span data-stu-id="28ae1-134">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="28ae1-135">kontener jednostek</span><span class="sxs-lookup"><span data-stu-id="28ae1-135">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="28ae1-136">klucz jednostki</span><span class="sxs-lookup"><span data-stu-id="28ae1-136">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="28ae1-137">zestaw jednostek</span><span class="sxs-lookup"><span data-stu-id="28ae1-137">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="28ae1-138">typ jednostki</span><span class="sxs-lookup"><span data-stu-id="28ae1-138">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="28ae1-139">aspekt</span><span class="sxs-lookup"><span data-stu-id="28ae1-139">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="28ae1-140">właściwość klucza obcego</span><span class="sxs-lookup"><span data-stu-id="28ae1-140">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="28ae1-141">funkcja zadeklarowana modelu</span><span class="sxs-lookup"><span data-stu-id="28ae1-141">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="28ae1-142">funkcja zdefiniowana przez model</span><span class="sxs-lookup"><span data-stu-id="28ae1-142">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="28ae1-143">właściwość nawigacji</span><span class="sxs-lookup"><span data-stu-id="28ae1-143">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="28ae1-144">właściwość</span><span class="sxs-lookup"><span data-stu-id="28ae1-144">property</span></span>](property.md)  
  
 [<span data-ttu-id="28ae1-145">ograniczenie integralności referencyjnej</span><span class="sxs-lookup"><span data-stu-id="28ae1-145">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="28ae1-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28ae1-146">See also</span></span>

- <span data-ttu-id="28ae1-147">[Narzędzia Entity Data Model ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="28ae1-147">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="28ae1-148">[Plik. edmx — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="28ae1-148">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="28ae1-149">Specyfikacja CSDL</span><span class="sxs-lookup"><span data-stu-id="28ae1-149">CSDL Specification</span></span>](./ef/language-reference/csdl-specification.md)
