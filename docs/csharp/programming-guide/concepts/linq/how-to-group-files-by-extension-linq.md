---
title: 'Instrukcje: Grupowanie plików według rozszerzenia (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 21a98320-a5a1-4981-82d8-6a637e7d9018
ms.openlocfilehash: 0b8cb30396a93f5f878c091c4aad3cab9db3f2d4
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584299"
---
# <a name="how-to-group-files-by-extension-linq-c"></a><span data-ttu-id="6e058-102">Instrukcje: Grupowanie plików według rozszerzenia (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6e058-102">How to: Group Files by Extension (LINQ) (C#)</span></span>
<span data-ttu-id="6e058-103">Ten przykład pokazuje, jak LINQ może służyć do wykonywania zaawansowanych grupowania i sortowania operacje na listach plików lub folderów.</span><span class="sxs-lookup"><span data-stu-id="6e058-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="6e058-104">Pokazano również, jak stronicować danych wyjściowych w oknie konsoli przy użyciu <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6e058-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e058-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e058-105">Example</span></span>  
 <span data-ttu-id="6e058-106">Następujące zapytanie pokazuje, jak, według których chcesz pogrupować zawartość drzewa katalogów określonego rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="6e058-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
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
  
 <span data-ttu-id="6e058-107">Dane wyjściowe z tego programu może być długi, w zależności od szczegółów lokalnego systemu plików i `startFolder` jest równa.</span><span class="sxs-lookup"><span data-stu-id="6e058-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="6e058-108">Aby umożliwić wyświetlanie wszystkich wyników, w tym przykładzie przedstawiono sposób przeglądania wyników.</span><span class="sxs-lookup"><span data-stu-id="6e058-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="6e058-109">Te same techniki można zastosować do aplikacji sieci Web i Windows.</span><span class="sxs-lookup"><span data-stu-id="6e058-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="6e058-110">Należy zauważyć, że ponieważ kod strony elementów w grupie, zagnieżdżoną `foreach` pętli jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="6e058-110">Notice that because the code pages the items in a group, a nested `foreach` loop is required.</span></span> <span data-ttu-id="6e058-111">Istnieje również logikę dodatkowe obliczenia bieżącej pozycji na liście i umożliwić użytkownikowi zatrzymać stronicowania i zakończyć program.</span><span class="sxs-lookup"><span data-stu-id="6e058-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="6e058-112">W tym konkretnym przypadku kwerendy stronicowania jest wykonywany dla pamięci podręcznej wyników z oryginalnego zapytania.</span><span class="sxs-lookup"><span data-stu-id="6e058-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="6e058-113">W innych kontekstach, takich jak LINQ to SQL takie pamięci podręcznej nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="6e058-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6e058-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6e058-114">Compiling the Code</span></span>  
 <span data-ttu-id="6e058-115">Tworzenie C# konsoli projekt aplikacji z `using` dyrektywy dla przestrzeni nazw System.Linq i System.IO.</span><span class="sxs-lookup"><span data-stu-id="6e058-115">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e058-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e058-116">See also</span></span>

- [<span data-ttu-id="6e058-117">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="6e058-117">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="6e058-118">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="6e058-118">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)
