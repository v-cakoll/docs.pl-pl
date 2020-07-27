---
title: LINQ to Objects (C#)
description: Dowiedz się więcej o LINQ to Objects w języku C#, które używają zapytań LINQ z dowolną kolekcją IEnumerable lub IEnumerable <T> bez pośredniego dostawcy LINQ lub interfejsu API.
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 7b67690ee13f207441bc94155acd91047b63b3df
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165550"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="dc2fd-103">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="dc2fd-103">LINQ to Objects (C#)</span></span>

<span data-ttu-id="dc2fd-104">Termin "LINQ to Objects" odnosi się do użycia zapytań LINQ z dowolnym <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcją bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dc2fd-104">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="dc2fd-105">Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601> , <xref:System.Array> lub <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="dc2fd-105">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="dc2fd-106">Kolekcja może być zdefiniowana przez użytkownika lub może być zwracana przez interfejs API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-106">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="dc2fd-107">W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-107">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="dc2fd-108">W stary sposób należy napisać złożone `foreach` pętle, które określają sposób pobierania danych z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-108">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="dc2fd-109">W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-109">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="dc2fd-110">Ponadto zapytania LINQ oferują trzy główne zalety przed tradycyjnymi `foreach` pętlami:</span><span class="sxs-lookup"><span data-stu-id="dc2fd-110">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
- <span data-ttu-id="dc2fd-111">Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-111">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
- <span data-ttu-id="dc2fd-112">Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-112">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
- <span data-ttu-id="dc2fd-113">Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-113">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="dc2fd-114">Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-114">In general, the more complex the operation you want to perform on the data, the more benefit you'll realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="dc2fd-115">Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-115">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="dc2fd-116">Nie jest to wyczerpujące.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-116">It's not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc2fd-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dc2fd-117">In This Section</span></span>  
 [<span data-ttu-id="dc2fd-118">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="dc2fd-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="dc2fd-119">Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-119">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="dc2fd-120">Zawiera również linki do artykułów demonstrujących te zasady.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-120">Also includes links to articles that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="dc2fd-121">LINQ i odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="dc2fd-121">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="dc2fd-122">Linki do przykładu, który pokazuje, jak LINQ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-122">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="dc2fd-123">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="dc2fd-123">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="dc2fd-124">Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-124">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="dc2fd-125">Zawiera również linki do artykułów, które przedstawiają te koncepcje.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-125">Also includes links to articles that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="dc2fd-126">Jak zbadać ArrayList za pomocą LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="dc2fd-126">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="dc2fd-127">Pokazuje, jak zbadać ArrayList w języku C#.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-127">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="dc2fd-128">Jak dodać metody niestandardowe dla zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="dc2fd-128">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="dc2fd-129">Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-129">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="dc2fd-130">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="dc2fd-130">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="dc2fd-131">Zawiera łącza do artykułów, które objaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.</span><span class="sxs-lookup"><span data-stu-id="dc2fd-131">Provides links to articles that explain LINQ and provide examples of code that perform queries.</span></span>
