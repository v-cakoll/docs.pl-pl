---
title: Jak wysyłać zapytania do zawartości plików tekstowych w folderze (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: f5b4dce7-1a34-4eb4-9bf1-60d5bdda264c
ms.openlocfilehash: 998fddd3f59ee64df9adcee1acc720d82861c3d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168742"
---
# <a name="how-to-query-the-contents-of-text-files-in-a-folder-linq-c"></a>Jak wysyłać zapytania do zawartości plików tekstowych w folderze (LINQ) (C#)
W tym przykładzie pokazano, jak zapytań o wszystkie pliki w drzewie określonego katalogu, otworzyć każdy plik i sprawdzić jego zawartość. Ten typ techniki może służyć do tworzenia indeksów lub odwrotnej indeksów zawartości drzewa katalogów. Wyszukiwanie ciągów prostych jest wykonywane w tym przykładzie. Jednak bardziej złożone typy dopasowywania wzorców można wykonywać za pomocą wyrażenia regularnego. Aby uzyskać więcej informacji, zobacz [Jak łączyć zapytania LINQ z wyrażeniami regularnymi (C#).](./how-to-combine-linq-queries-with-regular-expressions.md)  
  
## <a name="example"></a>Przykład  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
Utwórz projekt aplikacji konsoli `using` C# z dyrektywami dla system.Linq i System.IO przestrzeni nazw.
  
## <a name="see-also"></a>Zobacz też

- [LINQ i katalogi plików (C#)](./linq-and-file-directories.md)
- [LINQ do obiektów (C#)](./linq-to-objects.md)
