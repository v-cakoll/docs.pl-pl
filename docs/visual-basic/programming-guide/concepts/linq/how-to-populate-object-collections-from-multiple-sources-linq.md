---
title: "Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b52042078667ccfbefadcdf1cef5ab0873cc97b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a>Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)
W tym przykładzie przedstawiono sposób scalania danych z różnych źródeł w sekwencji nowych typów.  
  
> [!NOTE]
>  Nie należy próbować dołączyć dane w pamięci lub dane w systemie plików z danymi, które jest nadal w bazie danych. Takie sprzężenia między domenami może spowodować niezdefiniowane wyniki ze względu na różne sposoby, w którym można zdefiniować operacji łączenia dla zapytań bazy danych i innych źródeł. Ponadto istnieje ryzyko, że takie działanie może spowodować wyjątek braku pamięci, jeżeli jest wystarczająco duże ilości danych w bazie danych. Aby dołączyć dane z bazy danych do danych w pamięci, należy najpierw wywołać `ToList` lub `ToArray` w bazie danych zapytania, a następnie wykonaj sprzężenia w zwracanej kolekcji.  
  
### <a name="to-create-the-data-file"></a>Aby utworzyć plik danych  
  
-   Skopiuj pliki names.csv i scores.csv do folderu projektu, zgodnie z opisem w [porady: Dołącz zawartości z niepodobnych plików (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie typu o nazwie `Student` do przechowywania danych scalone z dwie kolekcje w pamięci ciągów symulujących danych z arkusza kalkulacyjnego w formacie CSV. Pierwsza kolekcja ciągów reprezentuje uczniów nazwy i identyfikatory, a druga kolekcja — identyfikator uczniów (w pierwszej kolumnie) i cztery egzaminu wyniki. Ten identyfikator jest używany jako klucz obcy.  
  
```vb  
Class Student  
    Public FirstName As String  
    Public LastName As String  
    Public ID As Integer  
    Public ExamScores As List(Of Integer)  
End Class  
  
Class PopulateCollection  
  
    Shared Sub Main()  
  
        ' Merge content from spreadsheets into a list of Student objects.  
  
        ' These data files are defined in How to: Join Content from   
        ' Dissimilar Files (LINQ).  
  
        ' Each line of names.csv consists of a last name, a first name, and an  
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111  
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")  
  
        ' Each line of scores.csv consists of an ID number and four test   
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60  
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")  
  
        ' The following query merges the content of two dissimilar spreadsheets   
        ' based on common ID values.  
        ' Multiple From clauses are used instead of a Join clause  
        ' in order to store the results of scoreLine.Split.  
        ' Note the dynamic creation of a list of integers for the  
        ' ExamScores member. We skip the first item in the split string   
        ' because it is the student ID, not an exam score.  
        Dim queryNamesScores = From nameLine In names  
                          Let splitName = nameLine.Split(New Char() {","})  
                          From scoreLine In scores  
                          Let splitScoreLine = scoreLine.Split(New Char() {","})  
                          Where splitName(2) = splitScoreLine(0)  
                          Select New Student() With {  
                               .FirstName = splitName(0), .LastName = splitName(1), .ID = splitName(2),  
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1  
                                             Select Convert.ToInt32(scoreAsText)).ToList()}  
  
        ' Optional. Store the query results for faster access in future  
        ' queries. This could be useful with very large data files.  
        Dim students As List(Of Student) = queryNamesScores.ToList()  
  
        ' Display each student's name and exam score average.  
        For Each s In students  
            Console.WriteLine("The average score of " & s.FirstName & " " &  
                              s.LastName & " is " & s.ExamScores.Average())  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
  
' Output:   
' The average score of Omelchenko Svetlana is 82.5  
' The average score of O'Donnell Claire is 72.25  
' The average score of Mortensen Sven is 84.5  
' The average score of Garcia Cesar is 88.25  
' The average score of Garcia Debra is 67  
' The average score of Fakhouri Fadi is 92.25  
' The average score of Feng Hanying is 88  
' The average score of Garcia Hugo is 85.75  
' The average score of Tucker Lance is 81.75  
' The average score of Adams Terry is 85.25  
' The average score of Zabokritski Eugene is 83  
' The average score of Tucker Michael is 92  
```  
  
 W [wybierz klauzuli](../../../../visual-basic/language-reference/queries/select-clause.md) , inicjatora obiektów jest używana do każdego nowego wystąpienia `Student` obiektu przy użyciu danych z dwóch źródeł.  
  
 Jeśli nie masz do przechowywania wyników zapytania, może być wygodniejsze niż nazwanymi typami typy anonimowe. Nazwane typy są wymagane w przypadku przekazania wyników zapytania poza metodą wykonywania zapytania. W poniższym przykładzie wykonuje to samo zadanie, co w poprzednim przykładzie, ale używa typy anonimowe zamiast typów o nazwie:  
  
```vb  
' Merge the data by using an anonymous type.   
' Note the dynamic creation of a list of integers for the  
' ExamScores member. We skip 1 because the first string  
' in the array is the student ID, not an exam score.  
Dim queryNamesScores2 =  
    From nameLine In names  
    Let splitName = nameLine.Split(New Char() {","})  
    From scoreLine In scores  
    Let splitScoreLine = scoreLine.Split(New Char() {","})  
    Where splitName(2) = splitScoreLine(0)  
    Select New With  
           {.Last = splitName(0),  
            .First = splitName(1),  
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1  
                           Select Convert.ToInt32(scoreAsText)).ToList()}  
  
' Display each student's name and exam score average.  
For Each s In queryNamesScores2  
    Console.WriteLine("The average score of " & s.First & " " &  
                      s.Last & " is " & s.ExamScores.Average())  
Next  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie projektu przeznaczonego dla programu .NET Framework w wersji 3.5 lub nowszego z odwołania do System.Core.dll i `Imports` instrukcji System.Linq przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ciągi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
