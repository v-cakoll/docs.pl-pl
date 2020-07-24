---
title: Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)
description: Dowiedz się, jak scalać dane z różnych źródeł w sekwencję nowych typów przy użyciu LINQ w języku C#. Te przykłady używają zarówno typów anonimowych, jak i nazwanych.
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 9dc9f98ae09e0fe3437b5d2ccab32b3dbcd93714
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104716"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a><span data-ttu-id="2dd5a-104">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="2dd5a-104">How to populate object collections from multiple sources (LINQ) (C#)</span></span>

<span data-ttu-id="2dd5a-105">Ten przykład pokazuje, jak scalać dane z różnych źródeł w sekwencję nowych typów.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-105">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="2dd5a-106">Nie należy próbować przyłączyć danych w pamięci lub danych w systemie plików o dane, które są nadal w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-106">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="2dd5a-107">Takie sprzężenia między domenami mogą dać niezdefiniowane wyniki, ponieważ różne sposoby, w których operacje Join mogą być zdefiniowane dla zapytań bazy danych i innych typów źródeł.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-107">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="2dd5a-108">Ponadto istnieje ryzyko, że takie działanie może spowodować wyjątek braku pamięci, jeśli ilość danych w bazie danych jest wystarczająco duża.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-108">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="2dd5a-109">Aby przyłączyć dane z bazy danych do danych znajdujących się w pamięci, najpierw należy wywołać `ToList` lub `ToArray` w kwerendzie bazy danych, a następnie wykonać sprzężenie w zwróconej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-109">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="2dd5a-110">Aby utworzyć plik danych</span><span class="sxs-lookup"><span data-stu-id="2dd5a-110">To create the data file</span></span>

<span data-ttu-id="2dd5a-111">Skopiuj pliki names.csv i scores.csv do folderu projektu, zgodnie z opisem w temacie [jak dołączyć zawartość z niepodobnych plików (LINQ) (C#](./how-to-join-content-from-dissimilar-files-linq.md)).</span><span class="sxs-lookup"><span data-stu-id="2dd5a-111">Copy the names.csv and scores.csv files into your project folder, as described in [How to join content from dissimilar files (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="2dd5a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2dd5a-112">Example</span></span>

<span data-ttu-id="2dd5a-113">Poniższy przykład pokazuje, jak używać nazwanego typu `Student` do przechowywania scalonych danych z dwóch kolekcji w pamięci ciągów, które symulują dane arkusza kalkulacyjnego w formacie CSV.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-113">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="2dd5a-114">Pierwszy zbiór ciągów reprezentuje nazwy uczniów i identyfikatory, a druga Kolekcja reprezentuje identyfikator ucznia (w pierwszej kolumnie) i cztery wyniki egzaminu.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-114">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="2dd5a-115">Identyfikator jest używany jako klucz obcy.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-115">The ID is used as the foreign key.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Student
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int ID { get; set; }
    public List<int> ExamScores { get; set; }
}

class PopulateCollection
{
    static void Main()
    {
        // These data files are defined in How to join content from
        // dissimilar files (LINQ).

        // Each line of names.csv consists of a last name, a first name, and an
        // ID number, separated by commas. For example, Omelchenko,Svetlana,111
        string[] names = System.IO.File.ReadAllLines(@"../../../names.csv");

        // Each line of scores.csv consists of an ID number and four test
        // scores, separated by commas. For example, 111, 97, 92, 81, 60
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");

        // Merge the data sources using a named type.
        // var could be used instead of an explicit type. Note the dynamic
        // creation of a list of ints for the ExamScores member. The first item
        // is skipped in the split string because it is the student ID,
        // not an exam score.
        IEnumerable<Student> queryNamesScores =
            from nameLine in names
            let splitName = nameLine.Split(',')
            from scoreLine in scores
            let splitScoreLine = scoreLine.Split(',')
            where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
            select new Student()
            {
                FirstName = splitName[0],
                LastName = splitName[1],
                ID = Convert.ToInt32(splitName[2]),
                ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                              select Convert.ToInt32(scoreAsText)).
                              ToList()
            };

        // Optional. Store the newly created student objects in memory
        // for faster access in future queries. This could be useful with
        // very large data files.
        List<Student> students = queryNamesScores.ToList();

        // Display each student's name and exam score average.
        foreach (var student in students)
        {
            Console.WriteLine("The average score of {0} {1} is {2}.",
                student.FirstName, student.LastName,
                student.ExamScores.Average());
        }

        //Keep console window open in debug mode
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}
/* Output:
    The average score of Omelchenko Svetlana is 82.5.
    The average score of O'Donnell Claire is 72.25.
    The average score of Mortensen Sven is 84.5.
    The average score of Garcia Cesar is 88.25.
    The average score of Garcia Debra is 67.
    The average score of Fakhouri Fadi is 92.25.
    The average score of Feng Hanying is 88.
    The average score of Garcia Hugo is 85.75.
    The average score of Tucker Lance is 81.75.
    The average score of Adams Terry is 85.25.
    The average score of Zabokritski Eugene is 83.
    The average score of Tucker Michael is 92.
 */
```

<span data-ttu-id="2dd5a-116">W klauzuli [SELECT](../../../language-reference/keywords/select-clause.md) Inicjator obiektu jest używany do tworzenia wystąpienia każdego nowego obiektu przy `Student` użyciu danych z dwóch źródeł.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-116">In the [select](../../../language-reference/keywords/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="2dd5a-117">Jeśli nie musisz przechowywać wyników zapytania, typy anonimowe mogą być wygodniejsze niż nazwane typy.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-117">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="2dd5a-118">Nazwane typy są wymagane, Jeśli przekażesz wyniki zapytania poza metodę, w której jest wykonywane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-118">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="2dd5a-119">Poniższy przykład wykonuje to samo zadanie jak w poprzednim przykładzie, ale używa typów anonimowych zamiast nazwanych:</span><span class="sxs-lookup"><span data-stu-id="2dd5a-119">The following example executes the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```csharp
// Merge the data sources by using an anonymous type.
// Note the dynamic creation of a list of ints for the
// ExamScores member. We skip 1 because the first string
// in the array is the student ID, not an exam score.
var queryNamesScores2 =
    from nameLine in names
    let splitName = nameLine.Split(',')
    from scoreLine in scores
    let splitScoreLine = scoreLine.Split(',')
    where Convert.ToInt32(splitName[2]) == Convert.ToInt32(splitScoreLine[0])
    select new
    {
        First = splitName[0],
        Last = splitName[1],
        ExamScores = (from scoreAsText in splitScoreLine.Skip(1)
                      select Convert.ToInt32(scoreAsText))
                      .ToList()
    };

// Display each student's name and exam score average.
foreach (var student in queryNamesScores2)
{
    Console.WriteLine("The average score of {0} {1} is {2}.",
        student.First, student.Last, student.ExamScores.Average());
}
```

## <a name="see-also"></a><span data-ttu-id="2dd5a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2dd5a-120">See also</span></span>

- [<span data-ttu-id="2dd5a-121">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="2dd5a-121">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="2dd5a-122">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="2dd5a-122">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="2dd5a-123">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="2dd5a-123">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
