---
title: 'Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
ms.openlocfilehash: 3ff51b0b5f04a44f83db2590bd7005097b1c0161
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323355"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a>Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)
W tym przykładzie przedstawiono sposób scalania danych z różnych źródeł w sekwencji nowych typów.  
  
> [!NOTE]
>  Nie należy próbować dołączyć dane w pamięci lub dane w systemie plików z danymi, które jest nadal w bazie danych. Takie sprzężenia między domenami może spowodować niezdefiniowane wyniki ze względu na różne sposoby, w którym można zdefiniować operacji łączenia dla zapytań bazy danych i innych źródeł. Ponadto istnieje ryzyko, że takie działanie może spowodować wyjątek braku pamięci, jeżeli jest wystarczająco duże ilości danych w bazie danych. Aby dołączyć dane z bazy danych do danych w pamięci, należy najpierw wywołać `ToList` lub `ToArray` w bazie danych zapytania, a następnie wykonaj sprzężenia w zwracanej kolekcji.  
  
### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych  
  
-   Skopiuj pliki names.csv i scores.csv do folderu projektu, zgodnie z opisem w [porady: Dołącz zawartości z plikami niepodobnych (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie typu o nazwie `Student` do przechowywania danych scalone z dwie kolekcje w pamięci ciągów symulujących danych z arkusza kalkulacyjnego w formacie CSV. Pierwsza kolekcja ciągów reprezentuje uczniów nazwy i identyfikatory, a druga kolekcja — identyfikator uczniów (w pierwszej kolumnie) i cztery egzaminu wyniki. Ten identyfikator jest używany jako klucz obcy.  
  
```csharp  
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
        // creation of a list of ints for the ExamScores member. We skip   
        // the first item in the split string because it is the student ID,   
        // not an exam score.  
        IEnumerable<Student> queryNamesScores =  
            from nameLine in names  
            let splitName = nameLine.Split(',')  
            from scoreLine in scores  
            let splitScoreLine = scoreLine.Split(',')  
            where splitName[2] == splitScoreLine[0]  
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
  
 W [wybierz](../../../../csharp/language-reference/keywords/select-clause.md) , inicjatora obiektów jest używana do każdego nowego wystąpienia `Student` obiektu przy użyciu danych z dwóch źródeł.  
  
 Jeśli nie masz do przechowywania wyników zapytania, może być wygodniejsze niż nazwanymi typami typy anonimowe. Nazwane typy są wymagane w przypadku przekazania wyników zapytania poza metodą wykonywania zapytania. W poniższym przykładzie wykonuje to samo zadanie, co w poprzednim przykładzie, ale używa typy anonimowe zamiast typów o nazwie:  
  
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
    where splitName[2] == splitScoreLine[0]  
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
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ciągi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [Inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
