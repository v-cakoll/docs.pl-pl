---
title: 'Instrukcje: Zbadaj zawartość plików tekstowych w folderze (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: ad0be3b4206d0aca649987bc3fbbc26102de77c4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592676"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a><span data-ttu-id="df7c8-102">Instrukcje: Zbadaj zawartość plików tekstowych w folderze (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="df7c8-102">How to: Query the Contents of Text Files in a Folder (LINQ) (C#)</span></span>
<span data-ttu-id="df7c8-103">Ten przykład pokazuje, jak badać wszystkie pliki w określonym drzewie katalogów, otwierać każdy plik i sprawdzać jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="df7c8-103">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="df7c8-104">Ten typ technika może służyć do tworzenia indeksów lub odwracania indeksów zawartości drzewa katalogów.</span><span class="sxs-lookup"><span data-stu-id="df7c8-104">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="df7c8-105">W tym przykładzie jest wykonywane proste wyszukiwanie ciągu.</span><span class="sxs-lookup"><span data-stu-id="df7c8-105">A simple string search is performed in this example.</span></span> <span data-ttu-id="df7c8-106">Jednak bardziej złożone typy dopasowywania do wzorców można wykonać przy użyciu wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="df7c8-106">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="df7c8-107">Aby uzyskać więcej informacji, zobacz [jak: Połącz zapytania LINQ z wyrażeniamiC#regularnymi](./how-to-combine-linq-queries-with-regular-expressions.md)().</span><span class="sxs-lookup"><span data-stu-id="df7c8-107">For more information, see [How to: Combine LINQ Queries with Regular Expressions (C#)](./how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df7c8-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="df7c8-108">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="df7c8-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="df7c8-109">Compiling the Code</span></span>  
<span data-ttu-id="df7c8-110">Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.</span><span class="sxs-lookup"><span data-stu-id="df7c8-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="df7c8-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df7c8-111">See also</span></span>

- [<span data-ttu-id="df7c8-112">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="df7c8-112">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
- [<span data-ttu-id="df7c8-113">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="df7c8-113">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
