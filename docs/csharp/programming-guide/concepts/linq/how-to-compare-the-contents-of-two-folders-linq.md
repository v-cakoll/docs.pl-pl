---
title: 'Instrukcje: Porównaj zawartość dwóch folderów (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: c7c4870e-c500-4de3-afa4-2c8e07f510e6
ms.openlocfilehash: f9f592eebb94ea783cff3ae3bc76125a9df72dd7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594066"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-c"></a><span data-ttu-id="4b279-102">Instrukcje: Porównaj zawartość dwóch folderów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b279-102">How to: Compare the Contents of Two Folders (LINQ) (C#)</span></span>
<span data-ttu-id="4b279-103">Ten przykład ilustruje trzy sposoby porównywania dwóch list plików:</span><span class="sxs-lookup"><span data-stu-id="4b279-103">This example demonstrates three ways to compare two file listings:</span></span>  
  
- <span data-ttu-id="4b279-104">Za pomocą zapytania o wartość logiczną określającą, czy dwie listy plików są identyczne.</span><span class="sxs-lookup"><span data-stu-id="4b279-104">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>  
  
- <span data-ttu-id="4b279-105">Wykonując zapytania dotyczące przecięcia do pobrania plików, które znajdują się w obu folderach.</span><span class="sxs-lookup"><span data-stu-id="4b279-105">By querying for the intersection to retrieve the files that are in both folders.</span></span>  
  
- <span data-ttu-id="4b279-106">Wykonując zapytania o różnicę zestawu, aby pobrać pliki znajdujące się w jednym folderze, ale nie w drugim.</span><span class="sxs-lookup"><span data-stu-id="4b279-106">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4b279-107">Techniki przedstawione w tym miejscu można dostosować do porównania sekwencji obiektów dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="4b279-107">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>  
  
 <span data-ttu-id="4b279-108">W `FileComparer` poniższej klasie pokazano, jak używać niestandardowej klasy porównującej ze standardowymi operatorami zapytań.</span><span class="sxs-lookup"><span data-stu-id="4b279-108">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="4b279-109">Klasa nie jest przeznaczona do użycia w rzeczywistych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="4b279-109">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="4b279-110">Po prostu używa nazwy i długości w bajtach każdego pliku, aby określić, czy zawartość każdego folderu jest identyczna, czy nie.</span><span class="sxs-lookup"><span data-stu-id="4b279-110">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="4b279-111">W rzeczywistym scenariuszu należy zmodyfikować tę funkcję porównującą w celu przeprowadzenia bardziej rygorystycznej kontroli równości.</span><span class="sxs-lookup"><span data-stu-id="4b279-111">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b279-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b279-112">Example</span></span>  
  
```csharp  
namespace QueryCompareTwoDirs  
{  
    class CompareDirs  
    {  
  
        static void Main(string[] args)  
        {  
  
            // Create two identical or different temporary folders   
            // on a local drive and change these file paths.  
            string pathA = @"C:\TestDir";  
            string pathB = @"C:\TestDir2";  
  
            System.IO.DirectoryInfo dir1 = new System.IO.DirectoryInfo(pathA);  
            System.IO.DirectoryInfo dir2 = new System.IO.DirectoryInfo(pathB);  
  
            // Take a snapshot of the file system.  
            IEnumerable<System.IO.FileInfo> list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
            IEnumerable<System.IO.FileInfo> list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
            //A custom file comparer defined below  
            FileCompare myFileCompare = new FileCompare();  
  
            // This query determines whether the two folders contain  
            // identical file lists, based on the custom file comparer  
            // that is defined in the FileCompare class.  
            // The query executes immediately because it returns a bool.  
            bool areIdentical = list1.SequenceEqual(list2, myFileCompare);  
  
            if (areIdentical == true)  
            {  
                Console.WriteLine("the two folders are the same");  
            }  
            else  
            {  
                Console.WriteLine("The two folders are not the same");  
            }  
  
            // Find the common files. It produces a sequence and doesn't   
            // execute until the foreach statement.  
            var queryCommonFiles = list1.Intersect(list2, myFileCompare);  
  
            if (queryCommonFiles.Count() > 0)  
            {  
                Console.WriteLine("The following files are in both folders:");  
                foreach (var v in queryCommonFiles)  
                {  
                    Console.WriteLine(v.FullName); //shows which items end up in result list  
                }  
            }  
            else  
            {  
                Console.WriteLine("There are no common files in the two folders.");  
            }  
  
            // Find the set difference between the two folders.  
            // For this example we only check one way.  
            var queryList1Only = (from file in list1  
                                  select file).Except(list2, myFileCompare);  
  
            Console.WriteLine("The following files are in list1 but not list2:");  
            foreach (var v in queryList1Only)  
            {  
                Console.WriteLine(v.FullName);  
            }  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
  
    // This implementation defines a very simple comparison  
    // between two FileInfo objects. It only compares the name  
    // of the files being compared and their length in bytes.  
    class FileCompare : System.Collections.Generic.IEqualityComparer<System.IO.FileInfo>  
    {  
        public FileCompare() { }  
  
        public bool Equals(System.IO.FileInfo f1, System.IO.FileInfo f2)  
        {  
            return (f1.Name == f2.Name &&  
                    f1.Length == f2.Length);  
        }  
  
        // Return a hash that reflects the comparison criteria. According to the   
        // rules for IEqualityComparer<T>, if Equals is true, then the hash codes must  
        // also be equal. Because equality as defined here is a simple value equality, not  
        // reference identity, it is possible that two or more objects will produce the same  
        // hash code.  
        public int GetHashCode(System.IO.FileInfo fi)  
        {  
            string s = $"{fi.Name}{fi.Length}";
            return s.GetHashCode();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b279-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4b279-113">Compiling the Code</span></span>  
 <span data-ttu-id="4b279-114">Utwórz projekt C# aplikacji konsolowej z `using` dyrektywami dotyczącymi przestrzeni nazw System. LINQ i system.IO.</span><span class="sxs-lookup"><span data-stu-id="4b279-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b279-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b279-115">See also</span></span>

- [<span data-ttu-id="4b279-116">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="4b279-116">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="4b279-117">LINQ i katalogi plików (C#)</span><span class="sxs-lookup"><span data-stu-id="4b279-117">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
