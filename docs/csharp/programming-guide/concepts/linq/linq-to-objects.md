---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 8c0eb71fffdd29d9599d74c789a66ec7caf1faeb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418176"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="86b9f-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="86b9f-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="86b9f-103">Termin "LINQ to Objects" odnosi się do używania zapytań LINQ z dowolnymi <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcji bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="86b9f-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="86b9f-104">Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601>, <xref:System.Array>lub <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="86b9f-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="86b9f-105">Kolekcja może być zdefiniowana przez użytkownika lub może być zwrócona przez interfejs API .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86b9f-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="86b9f-106">W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="86b9f-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="86b9f-107">W stary sposób należy napisać złożone pętle `foreach`, które określają sposób pobierania danych z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="86b9f-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="86b9f-108">W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.</span><span class="sxs-lookup"><span data-stu-id="86b9f-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="86b9f-109">Ponadto zapytania LINQ oferują trzy główne zalety w porównaniu z tradycyjnymi pętlami `foreach`:</span><span class="sxs-lookup"><span data-stu-id="86b9f-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="86b9f-110">Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.</span><span class="sxs-lookup"><span data-stu-id="86b9f-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="86b9f-111">Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86b9f-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="86b9f-112">Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="86b9f-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="86b9f-113">Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści, które można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.</span><span class="sxs-lookup"><span data-stu-id="86b9f-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="86b9f-114">Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami.</span><span class="sxs-lookup"><span data-stu-id="86b9f-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="86b9f-115">Nie jest to wyczerpujące.</span><span class="sxs-lookup"><span data-stu-id="86b9f-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86b9f-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="86b9f-116">In This Section</span></span>  
 [<span data-ttu-id="86b9f-117">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="86b9f-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="86b9f-118">Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="86b9f-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="86b9f-119">Zawiera również linki do tematów demonstrujących te zasady.</span><span class="sxs-lookup"><span data-stu-id="86b9f-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="86b9f-120">LINQ i odbicieC#()</span><span class="sxs-lookup"><span data-stu-id="86b9f-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="86b9f-121">Linki do przykładu, który pokazuje, jak LINQ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="86b9f-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="86b9f-122">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="86b9f-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="86b9f-123">Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików.</span><span class="sxs-lookup"><span data-stu-id="86b9f-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="86b9f-124">Zawiera również linki do tematów, które przedstawiają te koncepcje.</span><span class="sxs-lookup"><span data-stu-id="86b9f-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="86b9f-125">Instrukcje: zapytanie do ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="86b9f-125">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="86b9f-126">Pokazuje, jak zbadać ArrayList w C#.</span><span class="sxs-lookup"><span data-stu-id="86b9f-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="86b9f-127">Instrukcje: dodawanie metod niestandardowych dla zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="86b9f-127">How to: Add Custom Methods for LINQ Queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="86b9f-128">Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do interfejsu <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="86b9f-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="86b9f-129">Zapytanie zintegrowane z językiem (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="86b9f-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="86b9f-130">Zawiera łącza do tematów, które wyjaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.</span><span class="sxs-lookup"><span data-stu-id="86b9f-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
