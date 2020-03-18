---
title: Wykonywanie sprzężeń grupowanych (LINQ w języku C)Perform grouped joins (LINQ in C#)
description: Dowiedz się, jak wykonywać sprzężenia grupowe przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689141"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="68ca2-103">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="68ca2-103">Perform grouped joins</span></span>

<span data-ttu-id="68ca2-104">Sprzężenie grupy jest przydatne do tworzenia hierarchicznych struktur danych.</span><span class="sxs-lookup"><span data-stu-id="68ca2-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="68ca2-105">Łączy każdy element z pierwszej kolekcji z zestawem skorelowanych elementów z drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="68ca2-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="68ca2-106">Na przykład klasa lub tabela relacyjnej bazy danych o nazwie `Student` może zawierać dwa pola: `Id` i `Name`.</span><span class="sxs-lookup"><span data-stu-id="68ca2-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="68ca2-107">Druga klasa lub relacyjna `Course` tabela bazy `StudentId` danych `CourseTitle`o nazwie może zawierać dwa pola: i .</span><span class="sxs-lookup"><span data-stu-id="68ca2-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="68ca2-108">Dołączanie grupy z tych dwóch źródeł `Student.Id` `Course.StudentId`danych, na `Student` podstawie dopasowania `Course` i , będzie grupować każdy z kolekcji obiektów (które mogą być puste).</span><span class="sxs-lookup"><span data-stu-id="68ca2-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="68ca2-109">Każdy element pierwszej kolekcji pojawia się w zestawie wyników sprzężenia grupy, niezależnie od tego, czy skorelowane elementy znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="68ca2-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="68ca2-110">W przypadku, gdy nie znaleziono skorelowanych elementów, sekwencja skorelowanych elementów dla tego elementu jest pusta.</span><span class="sxs-lookup"><span data-stu-id="68ca2-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="68ca2-111">Selektor wyników ma zatem dostęp do każdego elementu pierwszej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="68ca2-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="68ca2-112">Różni się to od selektora wyników w sprzężeniu niegrupowym, który nie może uzyskać dostępu do elementów z pierwszej kolekcji, które nie mają dopasowania w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="68ca2-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="68ca2-113">Pierwszy przykład w tym artykule pokazuje, jak wykonać sprzężenie grupy.</span><span class="sxs-lookup"><span data-stu-id="68ca2-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="68ca2-114">Drugi przykład pokazuje, jak używać sprzężenia grupy do tworzenia elementów XML.</span><span class="sxs-lookup"><span data-stu-id="68ca2-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="68ca2-115">Przykład — dołączanie do grupy</span><span class="sxs-lookup"><span data-stu-id="68ca2-115">Example - Group join</span></span>

<span data-ttu-id="68ca2-116">Poniższy przykład wykonuje sprzężenie grupy `Person` obiektów `Pet` typu `Person` i `Pet.Owner` na podstawie pasujące jawłaściwości.</span><span class="sxs-lookup"><span data-stu-id="68ca2-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="68ca2-117">W przeciwieństwie do sprzężenia niegrupowego, które spowodowałoby parę elementów dla każdego dopasowania, sprzężenie grupy tworzy tylko jeden `Person` wynikowy obiekt dla każdego elementu pierwszej kolekcji, który w tym przykładzie jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="68ca2-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="68ca2-118">Odpowiednie elementy z drugiej kolekcji, które `Pet` w tym przykładzie są obiekty, są zgrupowane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="68ca2-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="68ca2-119">Na koniec funkcja selektora wyników tworzy typ anonimowy `Person.FirstName` dla każdego `Pet` dopasowania, który składa się z i kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="68ca2-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="68ca2-120">Przykład — dołączanie grupowe w celu utworzenia języka XML</span><span class="sxs-lookup"><span data-stu-id="68ca2-120">Example - Group join to create XML</span></span>

<span data-ttu-id="68ca2-121">Sprzężenia grupowe są idealne do tworzenia Języka XML przy użyciu LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="68ca2-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="68ca2-122">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że zamiast tworzyć typy anonimowe, funkcja selektora wyników tworzy elementy XML reprezentujące połączone obiekty.</span><span class="sxs-lookup"><span data-stu-id="68ca2-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="68ca2-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68ca2-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="68ca2-124">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="68ca2-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="68ca2-125">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="68ca2-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="68ca2-126">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="68ca2-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
