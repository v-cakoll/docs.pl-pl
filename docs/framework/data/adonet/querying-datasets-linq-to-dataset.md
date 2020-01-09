---
title: Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634784"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="1cfa4-102">Wykonywanie zapytania dotyczącego zestawów danych (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1cfa4-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="1cfa4-103">Po wypełnieniu <xref:System.Data.DataSet> obiektu za pomocą danych można rozpocząć wykonywanie zapytania.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="1cfa4-104">Formułowanie zapytań w LINQ to DataSet jest podobne do korzystania z funkcji CLR (Language-Integrated Query) dla innych źródeł danych obsługujących LINQ.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="1cfa4-105">Należy jednak pamiętać, że w przypadku korzystania z zapytań LINQ w obiekcie <xref:System.Data.DataSet> jest wysyłana kwerenda wyliczenia obiektów <xref:System.Data.DataRow> zamiast wyliczenia typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="1cfa4-106">Oznacza to, że można użyć dowolnego z elementów członkowskich klasy <xref:System.Data.DataRow> w zapytaniach LINQ.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="1cfa4-107">Dzięki temu można tworzyć rozbudowane, złożone zapytania.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="1cfa4-108">Podobnie jak w przypadku innych implementacji LINQ, można utworzyć zapytania LINQ to DataSet w dwóch różnych formularzach: składni wyrażeń zapytania i składni zapytania opartego na metodzie.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="1cfa4-109">Można użyć składni wyrażeń zapytania lub składni zapytania opartej na metodzie, aby wykonywać zapytania dotyczące pojedynczych tabel w <xref:System.Data.DataSet>, w przypadku wielu tabel w <xref:System.Data.DataSet>lub w odniesieniu do tabel w określonym <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cfa4-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1cfa4-110">In This Section</span></span>  
 [<span data-ttu-id="1cfa4-111">Zapytania jednotabelowe</span><span class="sxs-lookup"><span data-stu-id="1cfa4-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="1cfa4-112">Opisuje sposób wykonywania zapytań pojedynczej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="1cfa4-113">Zapytania wielotabelowe</span><span class="sxs-lookup"><span data-stu-id="1cfa4-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="1cfa4-114">Opisuje sposób wykonywania zapytań między tabelami.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="1cfa4-115">Wykonywanie zapytania do typizowanych zestawów danych</span><span class="sxs-lookup"><span data-stu-id="1cfa4-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="1cfa4-116">Opisuje sposób wykonywania zapytań dotyczących wpisanych obiektów <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1cfa4-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cfa4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cfa4-117">See also</span></span>

- [<span data-ttu-id="1cfa4-118">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1cfa4-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="1cfa4-119">Ładowanie danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="1cfa4-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
