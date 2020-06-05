---
title: LINQ do obiektów
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 1dca449f12c312fd395be56ebcb426c3a63b64d0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369066"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="f836e-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f836e-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="f836e-103">Termin "LINQ to Objects" odnosi się do użycia zapytań LINQ z dowolnym <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> kolekcją bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takiego jak [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ to XML](linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f836e-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](linq-to-xml.md).</span></span> <span data-ttu-id="f836e-104">Za pomocą LINQ można badać wszystkie wyliczalne kolekcje, takie jak <xref:System.Collections.Generic.List%601> , <xref:System.Array> lub <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="f836e-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="f836e-105">Kolekcja może być zdefiniowana przez użytkownika lub może być zwrócona przez interfejs API .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f836e-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="f836e-106">W podstawowym sensie LINQ to Objects reprezentuje nowe podejście do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f836e-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="f836e-107">W stary sposób należy napisać złożone `For Each` pętle, które określają sposób pobierania danych z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f836e-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="f836e-108">W podejściu LINQ napiszesz kod deklaratywny opisujący, co chcesz pobrać.</span><span class="sxs-lookup"><span data-stu-id="f836e-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="f836e-109">Ponadto zapytania LINQ oferują trzy główne zalety przed tradycyjnymi `For Each` pętlami:</span><span class="sxs-lookup"><span data-stu-id="f836e-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="f836e-110">Są one bardziej zwięzłe i czytelne, szczególnie w przypadku filtrowania wielu warunków.</span><span class="sxs-lookup"><span data-stu-id="f836e-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="f836e-111">Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f836e-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="f836e-112">Można je przenieść do innych źródeł danych z niewielką lub bez modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f836e-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="f836e-113">Ogólnie rzecz biorąc, bardziej złożone operacje, które mają być wykonywane na danych, tym większe korzyści, które można wykorzystać przy użyciu LINQ zamiast tradycyjnych technik iteracji.</span><span class="sxs-lookup"><span data-stu-id="f836e-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="f836e-114">Celem tej sekcji jest zademonstrowanie podejścia LINQ z pewnymi przykładami.</span><span class="sxs-lookup"><span data-stu-id="f836e-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="f836e-115">Nie jest to wyczerpujące.</span><span class="sxs-lookup"><span data-stu-id="f836e-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f836e-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f836e-116">In This Section</span></span>  
 [<span data-ttu-id="f836e-117">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f836e-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)  
 <span data-ttu-id="f836e-118">Wyjaśnia, w jaki sposób LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="f836e-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="f836e-119">Zawiera również linki do tematów demonstrujących te zasady.</span><span class="sxs-lookup"><span data-stu-id="f836e-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="f836e-120">LINQ i odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f836e-120">LINQ and Reflection (Visual Basic)</span></span>](linq-and-reflection.md)  
 <span data-ttu-id="f836e-121">Linki do przykładu, który pokazuje, jak LINQ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="f836e-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="f836e-122">LINQ i katalogi plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f836e-122">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)  
 <span data-ttu-id="f836e-123">Wyjaśnia, w jaki sposób LINQ może służyć do współdziałania z systemami plików.</span><span class="sxs-lookup"><span data-stu-id="f836e-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="f836e-124">Zawiera również linki do tematów, które przedstawiają te koncepcje.</span><span class="sxs-lookup"><span data-stu-id="f836e-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="f836e-125">Instrukcje: wykonywanie zapytań do ArrayList za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f836e-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="f836e-126">Pokazuje, jak zbadać ArrayList w języku C#.</span><span class="sxs-lookup"><span data-stu-id="f836e-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="f836e-127">Instrukcje: dodawanie metod niestandardowych dla zapytań LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f836e-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="f836e-128">Wyjaśnia, w jaki sposób rozszerzać zestaw metod, których można użyć dla zapytań LINQ przez dodanie metod rozszerzenia do <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f836e-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="f836e-129">Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f836e-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 <span data-ttu-id="f836e-130">Zawiera łącza do tematów, które wyjaśniają LINQ i dostarczają przykłady kodu, który wykonuje zapytania.</span><span class="sxs-lookup"><span data-stu-id="f836e-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
