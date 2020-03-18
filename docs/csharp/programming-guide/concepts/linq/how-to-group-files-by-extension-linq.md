---
title: Jak grupować pliki według rozszerzenia (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 2ee1fa1291f5845c818395dfe038ec5894adc863
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169158"
---
# <a name="how-to-group-files-by-extension-linq-c"></a>Jak grupować pliki według rozszerzenia (LINQ) (C#)
W tym przykładzie pokazano, jak LINQ może służyć do wykonywania zaawansowanych operacji grupowania i sortowania na listach plików lub folderów. Pokazuje również, jak strona dane wyjściowe w <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.Take%2A> oknie konsoli przy użyciu i metody.  
  
## <a name="example"></a>Przykład  
 W poniższej kwerendzie pokazano, jak pogrupować zawartość określonego drzewa katalogów według rozszerzenia nazwy pliku.  
  
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
  
 Dane wyjściowe z tego programu mogą być długie, w zależności od `startFolder` szczegółów lokalnego systemu plików i tego, na co jest ustawione. Aby włączyć wyświetlanie wszystkich wyników, w tym przykładzie pokazano, jak przeglądać wyniki. Te same techniki mogą być stosowane do aplikacji systemu Windows i sieci Web. Należy zauważyć, że ponieważ strony kodowe `foreach` elementów w grupie, zagnieżdżona pętla jest wymagana. Istnieje również dodatkowa logika do obliczania bieżącej pozycji na liście i umożliwienia użytkownikowi zatrzymania stronicowania i zakończenia programu. W tym konkretnym przypadku kwerenda stronicowania jest uruchamiana względem buforowanych wyników z oryginalnej kwerendy. W innych kontekstach, takich jak LINQ do SQL, takie buforowanie nie jest wymagane.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ do obiektów (C#)](./linq-to-objects.md)
- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
