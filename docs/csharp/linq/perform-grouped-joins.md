---
title: Wykonanie sprzężeń grupowanych (LINQ w C#)
description: Dowiedz się, jak wykonanie sprzężeń grupowanych za pomocą LINQ w C#.
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689141"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="533bc-103">Wykonywanie sprzężeń grupowanych</span><span class="sxs-lookup"><span data-stu-id="533bc-103">Perform grouped joins</span></span>

<span data-ttu-id="533bc-104">Sprzężenie grupy jest przydatne do tworzenia struktur danych hierarchicznych.</span><span class="sxs-lookup"><span data-stu-id="533bc-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="533bc-105">Pary on każdy element z kolekcji pierwszy zestaw elementów skorelowane z drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="533bc-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="533bc-106">Na przykład klasa lub tabela relacyjna baza danych o nazwie `Student` może zawierać dwóch pól: `Id` i `Name`.</span><span class="sxs-lookup"><span data-stu-id="533bc-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="533bc-107">Tabela drugiej klasy lub relacyjnej bazy danych o nazwie `Course` może zawierać dwóch pól: `StudentId` i `CourseTitle`.</span><span class="sxs-lookup"><span data-stu-id="533bc-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="533bc-108">Grupowe z tych dwóch źródeł danych, na podstawie zgodności `Student.Id` i `Course.StudentId`, czy każda grupa `Student` z kolekcją `Course` obiektów, (które mogą być puste).</span><span class="sxs-lookup"><span data-stu-id="533bc-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="533bc-109">Każdy element pierwszej kolekcji pojawia się w zestawie wyników grupowe, niezależnie od tego, czy elementy skorelowane znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="533bc-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="533bc-110">W przypadku, gdzie znajdują się żadnych elementów skorelowany sekwencji elementów skorelowany dla tego elementu jest pusty.</span><span class="sxs-lookup"><span data-stu-id="533bc-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="533bc-111">Selektor wynik zatem ma dostęp do każdego elementu pierwszej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="533bc-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="533bc-112">To różni się od selektor wynik sprzężenia-group, którego nie można uzyskać dostęp do elementów z pierwszej kolekcji, która ma niezgodności w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="533bc-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="533bc-113">Pierwszy przykład w tym artykule pokazano, jak wykonać sprzężenie grupy.</span><span class="sxs-lookup"><span data-stu-id="533bc-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="533bc-114">Drugi przykład przedstawia sposób użycia sprzężenie grupy do tworzenia elementów XML.</span><span class="sxs-lookup"><span data-stu-id="533bc-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="533bc-115">Przykład — łączenie grupowe</span><span class="sxs-lookup"><span data-stu-id="533bc-115">Example - Group join</span></span>

<span data-ttu-id="533bc-116">Poniższy przykład wykonuje sprzężenie grupy obiektów typu `Person` i `Pet` na podstawie `Person` dopasowania `Pet.Owner` właściwości.</span><span class="sxs-lookup"><span data-stu-id="533bc-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="533bc-117">W odróżnieniu od sprzężenia-group dałby w efekcie pary elementów dla każdego dopasowania, łączenie grupy tworzy tylko jeden obiekt wynikowy dla każdego elementu pierwszej kolekcji, czyli w tym przykładzie `Person` obiektu.</span><span class="sxs-lookup"><span data-stu-id="533bc-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="533bc-118">Odpowiednie elementy z kolekcji drugi, będące w tym przykładzie `Pet` obiektów są grupowane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="533bc-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="533bc-119">Ponadto funkcja selektor result tworzy typu anonimowego dla każdego dopasowania, która składa się z `Person.FirstName` i kolekcji `Pet` obiektów.</span><span class="sxs-lookup"><span data-stu-id="533bc-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="533bc-120">Przykład — łączenie grupowe tworzenie kodu XML</span><span class="sxs-lookup"><span data-stu-id="533bc-120">Example - Group join to create XML</span></span>

<span data-ttu-id="533bc-121">Sprzężenia grupowane są doskonałe do tworzenia XML za pomocą LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="533bc-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="533bc-122">Poniższy przykład jest podobny do poprzedniego przykładu, z tą różnicą, że zamiast tworzyć typy anonimowe, funkcja selektor result tworzy elementy XML, które reprezentują dołączonym do obiektów.</span><span class="sxs-lookup"><span data-stu-id="533bc-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="533bc-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="533bc-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="533bc-124">Wykonywanie sprzężeń wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="533bc-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="533bc-125">Wykonywanie lewych sprzężeń zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="533bc-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="533bc-126">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="533bc-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
