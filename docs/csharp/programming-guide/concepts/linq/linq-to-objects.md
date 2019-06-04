---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: c66a818d48316279817fdc6b7919a7667b6b8eb8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484466"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="e4ce9-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ce9-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="e4ce9-103">Termin "LINQ do obiektów" odnosi się do korzystania z LINQ zapytania ze wszystkimi <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcji bezpośrednio, bez użycia pośrednie dostawcy LINQ lub interfejsu API, takie jak [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e4ce9-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span></span> <span data-ttu-id="e4ce9-104">LINQ umożliwia zapytania wszelkie przeliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601>, <xref:System.Array>, lub <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="e4ce9-105">Kolekcja może być zdefiniowana przez użytkownika lub mogą być zwrócone przez interfejs API programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="e4ce9-106">W tym sensie podstawowe LINQ to Objects reprezentuje nowe podejście do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="e4ce9-107">W stary sposób było zapisać złożonych `foreach` pętli, które określa sposób pobierania danych z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="e4ce9-108">W przypadku zastosowania podejścia LINQ piszesz kod deklaratywny, opisujący, co ma zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="e4ce9-109">Ponadto zapytań LINQ oferuje trzy główne zalety w porównaniu z tradycyjnym `foreach` pętli:</span><span class="sxs-lookup"><span data-stu-id="e4ce9-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="e4ce9-110">Są one bardziej zwięzły, czytelny, szczególnie w przypadku, gdy wiele warunków filtrowania.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="e4ce9-111">Zapewniają zaawansowane filtrowanie, porządkowanie i możliwości przy minimalnej ilości kodu aplikacji grupowania.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="e4ce9-112">Można ich przenieść do innych źródeł danych przy użyciu niewielkich modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="e4ce9-113">Ogólnie rzecz biorąc, tym bardziej złożone operację, którą chcesz wykonać na danych, więcej korzyści będą weź pod uwagę przy użyciu LINQ zamiast iteracji tradycyjnych technik.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="e4ce9-114">Ta sekcja ma na celu wykazania podejście LINQ z przykładami wybierz.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="e4ce9-115">Nie ma niepełna.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4ce9-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e4ce9-116">In This Section</span></span>  
 [<span data-ttu-id="e4ce9-117">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ce9-117">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="e4ce9-118">W tym artykule wyjaśniono, jak LINQ może służyć do wykonywania zapytań i przekształcanie ciągów i zbiorów ciągów.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="e4ce9-119">Zawiera także łącza do tematów, które pokazują tych zasad.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="e4ce9-120">LINQ i odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ce9-120">LINQ and Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="e4ce9-121">Zawiera łącza do przykładu, który demonstruje, jak LINQ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="e4ce9-122">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ce9-122">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="e4ce9-123">W tym artykule wyjaśniono, jak LINQ może służyć do interakcji z systemami plików.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="e4ce9-124">Zawiera także łącza do tematów, które pokazują te pojęcia.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="e4ce9-125">Instrukcje: Zapytanie w ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ce9-125">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="e4ce9-126">Pokazuje, jak zapytanie w ArrayList w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="e4ce9-127">Instrukcje: Dodawanie metod niestandardowych do kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ce9-127">How to: Add Custom Methods for LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="e4ce9-128">Wyjaśnia, jak rozszerzyć zbiór metod, które służy do zapytań LINQ, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="e4ce9-129">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e4ce9-129">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="e4ce9-130">Zawiera łącza do tematów, które wyjaśniają LINQ i podają przykłady kodu, wykonujących zapytania.</span><span class="sxs-lookup"><span data-stu-id="e4ce9-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
