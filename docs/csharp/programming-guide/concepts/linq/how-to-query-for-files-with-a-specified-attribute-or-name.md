---
title: Jak wysyłać zapytania do plików o określonym atrybucie lub nazwie (C#)
ms.date: 07/20/2015
ms.assetid: 560e3879-b0b3-4549-ad02-0a53aff2f83c
ms.openlocfilehash: fc6456f159887b7ad109e8ad48f0f79999d53e09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168872"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-c"></a><span data-ttu-id="49546-102">Jak wysyłać zapytania do plików o określonym atrybucie lub nazwie (C#)</span><span class="sxs-lookup"><span data-stu-id="49546-102">How to query for files with a specified attribute or name (C#)</span></span>
<span data-ttu-id="49546-103">W tym przykładzie pokazano, jak znaleźć wszystkie pliki, które mają określone rozszerzenie nazwy pliku (na przykład ".txt") w określonym drzewie katalogów.</span><span class="sxs-lookup"><span data-stu-id="49546-103">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="49546-104">Pokazuje również, jak zwrócić najnowszy lub najstarszy plik w drzewie na podstawie czasu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="49546-104">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49546-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="49546-105">Example</span></span>  
  
```csharp  
class FindFileByExtension  
{  
    // This query will produce the full path for all .txt files  
    // under the specified folder including subfolders.  
    // It orders the list according to the file name.  
    static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        //Create the query  
        IEnumerable<System.IO.FileInfo> fileQuery =  
            from file in fileList  
            where file.Extension == ".txt"  
            orderby file.Name  
            select file;  
  
        //Execute the query. This might write out a lot of files!  
        foreach (System.IO.FileInfo fi in fileQuery)  
        {  
            Console.WriteLine(fi.FullName);  
        }  
  
        // Create and execute a new query by using the previous
        // query as a starting point. fileQuery is not
        // executed again until the call to Last()  
        var newestFile =  
            (from file in fileQuery  
             orderby file.CreationTime  
             select new { file.FullName, file.CreationTime })  
            .Last();  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}",  
            newestFile.FullName, newestFile.CreationTime);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49546-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="49546-106">Compiling the Code</span></span>  
  <span data-ttu-id="49546-107">Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="49546-107">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="49546-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49546-108">See also</span></span>

- [<span data-ttu-id="49546-109">LINQ do obiektów (C#)</span><span class="sxs-lookup"><span data-stu-id="49546-109">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="49546-110">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="49546-110">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
