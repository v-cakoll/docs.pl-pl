---
title: Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 3d841e5ca25afde94674af0fedc9a824c382be5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345756"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)

W tym przykładzie pokazano, jak scalić dane z różnych źródeł w sekwencję nowych typów.

> [!NOTE]
> Nie próbuj dołączać danych ani danych w pamięci w systemie plików z danymi, które nadal są w bazie danych. Takie sprzężenia między domenami mogą dawać niezdefiniowane wyniki z powodu różnych sposobów, w jaki operacje sprzężenia mogą być zdefiniowane dla kwerend bazy danych i innych typów źródeł. Ponadto istnieje ryzyko, że taka operacja może spowodować wyjątek braku pamięci, jeśli ilość danych w bazie danych jest wystarczająco duża. Aby dołączyć dane z bazy danych do `ToList` danych `ToArray` w pamięci, najpierw wywołać lub na kwerendzie bazy danych, a następnie wykonać sprzężenie na zwróconej kolekcji.

## <a name="to-create-the-data-file"></a>Aby utworzyć plik danych

Skopiuj pliki names.csv i scores.csv do folderu projektu, zgodnie z opisem w [jak dołączyć zawartość z różnych plików (LINQ) (C#)](./how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `Student` jak używać nazwanego typu do przechowywania scalonych danych z dwóch kolekcji ciągów w pamięci, które symulują dane arkusza kalkulacyjnego w formacie csv. Pierwsza kolekcja ciągów reprezentuje nazwy i identyfikatory uczniów, a druga kolekcja reprezentuje identyfikator ucznia (w pierwszej kolumnie) i cztery wyniki egzaminu. Identyfikator jest używany jako klucz obcy.

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

W [select](../../../language-reference/keywords/select-clause.md) klauzuli inicjatora obiektu jest używany `Student` do tworzenia wystąpienia każdego nowego obiektu przy użyciu danych z dwóch źródeł.

Jeśli nie musisz przechowywać wyniki kwerendy, typy anonimowe mogą być wygodniejsze niż typy nazwane. Nazwane typy są wymagane, jeśli wyniki kwerendy są wymagane poza metodą, w której kwerenda jest wykonywana. Poniższy przykład wykonuje to samo zadanie co poprzedni przykład, ale używa typów anonimowych zamiast nazwanych typów:

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

## <a name="see-also"></a>Zobacz też

- [LINQ i ciągi (C#)](./linq-and-strings.md)
- [Inicjatory obiektów i kolekcji](../../classes-and-structs/object-and-collection-initializers.md)
- [Typy anonimowe](../../classes-and-structs/anonymous-types.md)
