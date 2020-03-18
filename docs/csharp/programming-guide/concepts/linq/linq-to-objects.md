---
title: LINQ do obiektów (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344781"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="333e4-102">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="333e4-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="333e4-103">Termin "LINQ do obiektów" odnosi się do korzystania <xref:System.Collections.IEnumerable> z <xref:System.Collections.Generic.IEnumerable%601> zapytań LINQ z dowolnym lub kolekcji bezpośrednio, bez użycia pośredniego dostawcy LINQ lub interfejsu API, takich jak [LINQ do SQL](../../../../framework/data/adonet/sql/linq/index.md) lub [LINQ do XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="333e4-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="333e4-104">Linq służy do wykonywania zapytań do <xref:System.Collections.Generic.List%601> <xref:System.Array>wszystkich <xref:System.Collections.Generic.Dictionary%602>kolekcji wyliczanych, takich jak , , lub .</span><span class="sxs-lookup"><span data-stu-id="333e4-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="333e4-105">Kolekcja może być zdefiniowana przez użytkownika lub może być zwracana przez interfejs API .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="333e4-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="333e4-106">W sensie podstawowym LINQ do obiektów reprezentuje nowe podejście do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="333e4-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="333e4-107">W stary sposób trzeba było `foreach` napisać złożone pętle, które określały sposób pobierania danych z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="333e4-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="333e4-108">W podejściu LINQ piszesz kod deklaratywny, który opisuje, co chcesz pobrać.</span><span class="sxs-lookup"><span data-stu-id="333e4-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="333e4-109">Ponadto zapytania LINQ oferują trzy główne `foreach` zalety w porównaniu z tradycyjnymi pętlami:</span><span class="sxs-lookup"><span data-stu-id="333e4-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="333e4-110">Są one bardziej zwięzłe i czytelne, zwłaszcza podczas filtrowania wielu warunków.</span><span class="sxs-lookup"><span data-stu-id="333e4-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="333e4-111">Zapewniają one zaawansowane możliwości filtrowania, porządkowania i grupowania przy minimalnym kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="333e4-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="333e4-112">Mogą być przenoszeni do innych źródeł danych z niewielkimi lub żadnymi modyfikacjami.</span><span class="sxs-lookup"><span data-stu-id="333e4-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="333e4-113">Ogólnie rzecz biorąc bardziej złożona operacja, którą chcesz wykonać na danych, tym więcej korzyści zrealizujesz przy użyciu LINQ zamiast tradycyjnych technik iteracji.</span><span class="sxs-lookup"><span data-stu-id="333e4-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="333e4-114">Celem tej sekcji jest wykazanie podejścia LINQ z niektórych przykładów wybierz.</span><span class="sxs-lookup"><span data-stu-id="333e4-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="333e4-115">Nie ma być wyczerpujący.</span><span class="sxs-lookup"><span data-stu-id="333e4-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="333e4-116">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="333e4-116">In This Section</span></span>  
 [<span data-ttu-id="333e4-117">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="333e4-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="333e4-118">W tym artykule wyjaśniono, jak LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="333e4-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="333e4-119">Zawiera również linki do tematów, które pokazują te zasady.</span><span class="sxs-lookup"><span data-stu-id="333e4-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="333e4-120">LINQ i odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="333e4-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="333e4-121">Łącza do próbki, która pokazuje, jak LINQ używa odbicia.</span><span class="sxs-lookup"><span data-stu-id="333e4-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="333e4-122">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="333e4-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="333e4-123">W tym artykule wyjaśniono, w jaki sposób linq może służyć do interakcji z systemami plików.</span><span class="sxs-lookup"><span data-stu-id="333e4-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="333e4-124">Zawiera również łącza do tematów, które pokazują te pojęcia.</span><span class="sxs-lookup"><span data-stu-id="333e4-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="333e4-125">Jak zapytanie ArrayList z LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="333e4-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="333e4-126">Pokazuje, jak zapytanie ArrayList w języku C#.</span><span class="sxs-lookup"><span data-stu-id="333e4-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="333e4-127">Jak dodać metody niestandardowe dla zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="333e4-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="333e4-128">W tym artykule wyjaśniono, jak rozszerzyć zestaw metod, których można <xref:System.Collections.Generic.IEnumerable%601> używać dla kwerend LINQ, dodając metody rozszerzenia do interfejsu.</span><span class="sxs-lookup"><span data-stu-id="333e4-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="333e4-129">Zapytanie zintegrowane z językiem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="333e4-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="333e4-130">Zawiera łącza do tematów, które wyjaśniają LINQ i podać przykłady kodu, który wykonuje kwerendy.</span><span class="sxs-lookup"><span data-stu-id="333e4-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
