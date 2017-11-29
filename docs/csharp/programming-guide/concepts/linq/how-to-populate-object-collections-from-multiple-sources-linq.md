---
title: "Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ad7d480-b46c-4ccc-8c57-76f2d04ccc6d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3d3f0f9380e13addac38e32d4cc095d60e19bcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-c"></a><span data-ttu-id="c4fb7-102">Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c4fb7-102">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>
<span data-ttu-id="c4fb7-103">W tym przykładzie przedstawiono sposób scalania danych z różnych źródeł w sekwencji nowych typów.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-103">This example shows how to merge data from different sources into a sequence of new types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4fb7-104">Nie należy próbować dołączyć dane w pamięci lub dane w systemie plików z danymi, które jest nadal w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-104">Do not try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="c4fb7-105">Takie sprzężenia między domenami może spowodować niezdefiniowane wyniki ze względu na różne sposoby, w którym można zdefiniować operacji łączenia dla zapytań bazy danych i innych źródeł.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-105">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="c4fb7-106">Ponadto istnieje ryzyko, że takie działanie może spowodować wyjątek braku pamięci, jeżeli jest wystarczająco duże ilości danych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-106">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="c4fb7-107">Aby dołączyć dane z bazy danych do danych w pamięci, należy najpierw wywołać `ToList` lub `ToArray` w bazie danych zapytania, a następnie wykonaj sprzężenia w zwracanej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-107">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="c4fb7-108">Aby utworzyć plik danych</span><span class="sxs-lookup"><span data-stu-id="c4fb7-108">To create the data file</span></span>  
  
-   <span data-ttu-id="c4fb7-109">Skopiuj pliki names.csv i scores.csv do folderu projektu, zgodnie z opisem w [porady: Dołącz zawartości z plikami niepodobnych (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="c4fb7-109">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4fb7-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4fb7-110">Example</span></span>  
 <span data-ttu-id="c4fb7-111">Poniższy przykład przedstawia użycie typu o nazwie `Student` do przechowywania danych scalone z dwie kolekcje w pamięci ciągów symulujących danych z arkusza kalkulacyjnego w formacie CSV.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-111">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="c4fb7-112">Pierwsza kolekcja ciągów reprezentuje uczniów nazwy i identyfikatory, a druga kolekcja — identyfikator uczniów (w pierwszej kolumnie) i cztery egzaminu wyniki.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-112">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="c4fb7-113">Ten identyfikator jest używany jako klucz obcy.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-113">The ID is used as the foreign key.</span></span>  
  
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
  
 <span data-ttu-id="c4fb7-114">W [wybierz](../../../../csharp/language-reference/keywords/select-clause.md) , inicjatora obiektów jest używana do każdego nowego wystąpienia `Student` obiektu przy użyciu danych z dwóch źródeł.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-114">In the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>  
  
 <span data-ttu-id="c4fb7-115">Jeśli nie masz do przechowywania wyników zapytania, może być wygodniejsze niż nazwanymi typami typy anonimowe.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-115">If you do not have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="c4fb7-116">Nazwane typy są wymagane w przypadku przekazania wyników zapytania poza metodą wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-116">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="c4fb7-117">W poniższym przykładzie wykonuje to samo zadanie, co w poprzednim przykładzie, ale używa typy anonimowe zamiast typów o nazwie:</span><span class="sxs-lookup"><span data-stu-id="c4fb7-117">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4fb7-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c4fb7-118">Compiling the Code</span></span>  
 <span data-ttu-id="c4fb7-119">Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="c4fb7-119">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fb7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4fb7-120">See Also</span></span>  
 [<span data-ttu-id="c4fb7-121">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="c4fb7-121">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="c4fb7-122">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="c4fb7-122">Object and Collection Initializers</span></span>](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="c4fb7-123">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="c4fb7-123">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
