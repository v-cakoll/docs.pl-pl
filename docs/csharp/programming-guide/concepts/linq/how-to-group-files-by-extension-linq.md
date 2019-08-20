---
title: 'Instrukcje: Grupuj pliki według rozszerzenia (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: aa3e428a4655bfcc0707e111da3ca6206a2b9596
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593252"
---
# <a name="how-to-group-files-by-extension-linq-c"></a>Instrukcje: Grupuj pliki według rozszerzenia (LINQ) (C#)
Ten przykład pokazuje, jak LINQ może służyć do wykonywania zaawansowanych operacji grupowania i sortowania na listach plików lub folderów. Przedstawiono w nim również sposób wyświetlania stron wyjściowych w oknie konsoli przy użyciu <xref:System.Linq.Enumerable.Skip%2A> metod <xref:System.Linq.Enumerable.Take%2A> i.  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie pokazuje, jak grupować zawartość określonego drzewa katalogów według rozszerzenia nazwy pliku.  
  
```csharp  
class GroupByExtension  
{  
    // This query will sort all the files under the specified folder  
    //  and subfolder into groups keyed by the file extension.  
    private static void Main()  
    {  
        // Take a snapshot of the file system.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Used in WriteLine to trim output lines.  
        int trimLength = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Create the query.  
        var queryGroupByExt =  
            from file in fileList  
            group file by file.Extension.ToLower() into fileGroup  
            orderby fileGroup.Key  
            select fileGroup;  
  
        // Display one group at a time. If the number of   
        // entries is greater than the number of lines  
        // in the console window, then page the output.  
        PageOutput(trimLength, queryGroupByExt);  
    }  
  
    // This method specifically handles group queries of FileInfo objects with string keys.  
    // It can be modified to work for any long listings of data. Note that explicit typing  
    // must be used in method signatures. The groupbyExtList parameter is a query that produces  
    // groups of FileInfo objects with string keys.  
    private static void PageOutput(int rootLength,  
                                    IEnumerable<System.Linq.IGrouping<string, System.IO.FileInfo>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine(filegroup.Key == String.Empty ? "[none]" : filegroup.Key);  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var f in resultPage)  
                {  
                    Console.WriteLine("\t{0}", f.FullName.Substring(rootLength));  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 Dane wyjściowe tego programu mogą być długie, w zależności od szczegółów lokalnego systemu plików i `startFolder` konfiguracji. Aby umożliwić wyświetlanie wszystkich wyników, ten przykład pokazuje, jak przechodzić przez wyniki. Te same techniki można stosować do aplikacji systemu Windows i sieci Web. Zauważ, że ponieważ strona kodowa zawiera elementy w grupie, wymagana jest `foreach` pętla zagnieżdżona. Istnieje również dodatkowa logika służąca do obliczania bieżącej pozycji na liście i umożliwia użytkownikowi zatrzymanie stronicowania i wyjście z programu. W tym konkretnym przypadku kwerenda stronicowania jest uruchamiana względem wyników z pamięci podręcznej z oryginalnego zapytania. W innych kontekstach, takich jak LINQ to SQL, takie buforowanie nie jest wymagane.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Objects (C#)](./linq-to-objects.md)
- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
