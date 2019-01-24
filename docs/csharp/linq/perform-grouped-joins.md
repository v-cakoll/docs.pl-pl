---
title: Wykonanie sprzężeń grupowanych (LINQ w C#)
description: Dowiedz się, jak wykonanie sprzężeń grupowanych za pomocą LINQ w C#.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: d8a2d7bbbe78d3fc1f2518e057ade5045cee43e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511832"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="87605-103">Wykonanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="87605-103">Perform grouped joins</span></span>

<span data-ttu-id="87605-104">Sprzężenie grupy jest przydatne do tworzenia struktur danych hierarchicznych.</span><span class="sxs-lookup"><span data-stu-id="87605-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="87605-105">Pary on każdy element z kolekcji pierwszy zestaw elementów skorelowane z drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87605-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="87605-106">Na przykład klasa lub tabela relacyjna baza danych o nazwie `Student` może zawierać dwóch pól: `Id` i `Name`.</span><span class="sxs-lookup"><span data-stu-id="87605-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="87605-107">Tabela drugiej klasy lub relacyjnej bazy danych o nazwie `Course` może zawierać dwóch pól: `StudentId` i `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="87605-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="87605-108">Grupowe z tych dwóch źródeł danych, na podstawie zgodności `Student.Id` i `Course.StudentId`, czy każda grupa `Student` z kolekcją `Course` obiektów, (które mogą być puste).</span><span class="sxs-lookup"><span data-stu-id="87605-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="87605-109">Każdy element pierwszej kolekcji pojawia się w zestawie wyników grupowe, niezależnie od tego, czy elementy skorelowane znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87605-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="87605-110">W przypadku, gdzie znajdują się żadnych elementów skorelowany sekwencji elementów skorelowany dla tego elementu jest pusty.</span><span class="sxs-lookup"><span data-stu-id="87605-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="87605-111">Selektor wynik zatem ma dostęp do każdego elementu pierwszej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87605-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="87605-112">To różni się od selektor wynik sprzężenia-group, którego nie można uzyskać dostęp do elementów z pierwszej kolekcji, która ma niezgodności w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87605-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="87605-113">Pierwszy przykład w tym artykule pokazano, jak wykonać sprzężenie grupy.</span><span class="sxs-lookup"><span data-stu-id="87605-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="87605-114">Drugi przykład przedstawia sposób użycia sprzężenie grupy do tworzenia elementów XML.</span><span class="sxs-lookup"><span data-stu-id="87605-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="87605-115">Przykład — łączenie grupowe</span><span class="sxs-lookup"><span data-stu-id="87605-115">Example - Group join</span></span>

<span data-ttu-id="87605-116">Poniższy przykład wykonuje sprzężenie grupy obiektów typu `Person` i `Pet` na podstawie `Person` dopasowania `Pet.Owner` właściwości.</span><span class="sxs-lookup"><span data-stu-id="87605-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="87605-117">W odróżnieniu od sprzężenia-group dałby w efekcie pary elementów dla każdego dopasowania, łączenie grupy tworzy tylko jeden obiekt wynikowy dla każdego elementu pierwszej kolekcji, czyli w tym przykładzie `Person` obiektu.</span><span class="sxs-lookup"><span data-stu-id="87605-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="87605-118">Odpowiednie elementy z kolekcji drugi, będące w tym przykładzie `Pet` obiektów są grupowane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="87605-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="87605-119">Ponadto funkcja selektor result tworzy typu anonimowego dla każdego dopasowania, która składa się z `Person.FirstName` i kolekcji `Pet` obiektów.</span><span class="sxs-lookup"><span data-stu-id="87605-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="87605-120">Przykład — łączenie grupowe tworzenie kodu XML</span><span class="sxs-lookup"><span data-stu-id="87605-120">Example - Group join to create XML</span></span>

<span data-ttu-id="87605-121">Sprzężenia grupowane są doskonałe do tworzenia XML za pomocą LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="87605-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="87605-122">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że zamiast tworzyć typy anonimowe, funkcja selektor result tworzy elementy XML, które reprezentują dołączonym do obiektów.</span><span class="sxs-lookup"><span data-stu-id="87605-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="87605-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87605-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="87605-124">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="87605-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="87605-125">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="87605-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="87605-126">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="87605-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
