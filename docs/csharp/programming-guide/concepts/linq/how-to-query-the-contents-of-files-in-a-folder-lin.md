---
title: Jak zbadać zawartość plików tekstowych w folderze (LINQ) (C#)
description: Dowiedz się, jak za pomocą LINQ w języku C# wykonać zapytania dotyczące wszystkich plików w drzewie katalogów, otworzyć każdy plik i zbadać jego zawartość.
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 216edc2ee6fc43fd06a3c89b1b6b73f693f752f8
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104263"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="85559-103">Jak zbadać zawartość plików tekstowych w folderze (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="85559-103">How to query the contents of text files in a folder (LINQ) (C#)</span></span>
<span data-ttu-id="85559-104">Ten przykład pokazuje, jak badać wszystkie pliki w określonym drzewie katalogów, otwierać każdy plik i sprawdzać jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="85559-104">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="85559-105">Ten typ technika może służyć do tworzenia indeksów lub odwracania indeksów zawartości drzewa katalogów.</span><span class="sxs-lookup"><span data-stu-id="85559-105">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="85559-106">W tym przykładzie jest wykonywane proste wyszukiwanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="85559-106">A simple string search is performed in this example.</span></span> <span data-ttu-id="85559-107">Jednak bardziej złożone typy dopasowywania do wzorców można wykonać przy użyciu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="85559-107">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="85559-108">Aby uzyskać więcej informacji, zobacz [jak łączyć zapytania LINQ z wyrażeniami regularnymi (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="85559-108">For more information, see [How to combine LINQ queries with regular expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85559-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="85559-109">Example</span></span>  
  
```csharp  
class QueryContents  
{  
    public static void Main()  
    {  
        // Modify this path as necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        string searchTerm = @"Visual Studio";  
  
        // Search the contents of each file.  
        // A regular expression created with the RegEx class  
        // could be used instead of the Contains method.  
        // queryMatchingFiles is an IEnumerable<string>.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = GetFileText(file.FullName)  
            where fileText.Contains(searchTerm)  
            select file.FullName;  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm);  
        foreach (string filename in queryMatchingFiles)  
        {  
            Console.WriteLine(filename);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Read the contents of the file.  
    static string GetFileText(string name)  
    {  
        string fileContents = String.Empty;  
  
        // If the file has been deleted since we took
        // the snapshot, ignore it and return the empty string.  
        if (System.IO.File.Exists(name))  
        {  
            fileContents = System.IO.File.ReadAllText(name);  
        }  
        return fileContents;  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85559-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="85559-110">Compiling the Code</span></span>  
<span data-ttu-id="85559-111">Utwórz projekt aplikacji konsolowej w języku C# z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.</span><span class="sxs-lookup"><span data-stu-id="85559-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="85559-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85559-112">See also</span></span>

- [<span data-ttu-id="85559-113">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="85559-113">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="85559-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="85559-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
