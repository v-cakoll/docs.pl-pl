---
title: 'Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)'
ms.date: 06/12/2018
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: a40ff5ddcf606b0de8a1f41d96523526dc849462
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702077"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)

W tym przykładzie przedstawiono sposób scalania danych z różnych źródeł w sekwencji nowych typów.

> [!NOTE]
> Nie należy próbować dołączyć dane w pamięci lub dane w systemie plików z danymi, które są nadal w bazie danych. Takie sprzężeń między domenami może przynieść niezdefiniowane wyniki ze względu na różne sposoby, w którym można zdefiniować operacji łączenia zapytań bazy danych i innych typów źródeł. Ponadto istnieje ryzyko, takie działanie może spowodować wyjątek braku pamięci, gdy ilość danych w bazie danych jest wystarczająco duży. Aby dołączyć dane z bazy danych do danych w pamięci, należy najpierw wywołać `ToList` lub `ToArray` w bazie danych zapytania, a następnie wykonaj sprzężenia na zwrócona kolekcja.

## <a name="to-create-the-data-file"></a>Aby utworzyć plik danych

Skopiuj pliki names.csv i scores.csv w folderze projektu, zgodnie z opisem w [jak: Łączenie zawartości niepodobnych plików (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać typu nazwanego `Student` do przechowywania scalane dane z dwóch kolekcji w pamięci ciągów, które symulują dane arkusza kalkulacyjnego w formacie CSV. Pierwsza kolekcja ciągów reprezentuje identyfikatory i nazwy studentów, a druga kolekcja reprezentuje identyfikator uczniów (w pierwszej kolumnie) i cztery wyniki egzamin. Identyfikator jest używany jako klucza obcego.

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
        // These data files are defined in How to: Join Content from
        // Dissimilar Files (LINQ).

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

W [wybierz](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli inicjatora obiektu jest używany do utworzenia wystąpienia każdy nowość `Student` obiektu przy użyciu danych z dwóch źródeł.

Jeśli nie masz do przechowywania wyników zapytania, typy anonimowe może być bardziej wygodne niż nazwane typy. Nazwane typy są wymagane w przypadku przekazania wyników zapytania, poza metodą wykonywania zapytania. Poniższy przykład wykonuje tego samego zadania, jak w poprzednim przykładzie, ale używa typów anonimowych zamiast nazwane typy:

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

## <a name="compiling-the-code"></a>Kompilowanie kodu

Utwórz i skompiluj projekt, który jest przeznaczony dla jednego z następujących opcji:

- .NET framework w wersji 3.5 za pomocą odwołania do System.Core.dll.
- .NET framework w wersji 4.0 lub nowszy.
- .NET core w wersji 1.0 lub nowszej.

## <a name="see-also"></a>Zobacz także

- [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
- [Inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [Typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
