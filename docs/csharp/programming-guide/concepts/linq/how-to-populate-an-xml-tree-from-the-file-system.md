---
title: Jak wypełnić drzewo XML z systemu plików (C#)
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: beb44be1a787fa09b091aa48022dbb5b10c4632b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345780"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="cf5f3-102">Jak wypełnić drzewo XML z systemu plików (C#)</span><span class="sxs-lookup"><span data-stu-id="cf5f3-102">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="cf5f3-103">Typową i użyteczną aplikacją drzew XML jest hierarchiczny magazyn danych nazw/wartości.</span><span class="sxs-lookup"><span data-stu-id="cf5f3-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="cf5f3-104">Można wypełnić drzewo XML danymi hierarchicznymi, a następnie wykonać do nich zapytania, przekształcić je i w razie potrzeby serializować.</span><span class="sxs-lookup"><span data-stu-id="cf5f3-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="cf5f3-105">W tym scenariuszu użycia wiele semantyki specyficznych dla XML, takich jak przestrzeń nazw i zachowanie białych znaków, nie są ważne.</span><span class="sxs-lookup"><span data-stu-id="cf5f3-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="cf5f3-106">Zamiast tego używasz drzewa XML jako małej, w pamięci, hierarchicznej bazy danych pojedynczego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cf5f3-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf5f3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf5f3-107">Example</span></span>  
 <span data-ttu-id="cf5f3-108">Poniższy przykład wypełnia drzewo XML z lokalnego systemu plików przy użyciu rekursji.</span><span class="sxs-lookup"><span data-stu-id="cf5f3-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="cf5f3-109">Następnie wykonuje zapytanie do drzewa, obliczając łączny rozmiar wszystkich plików w drzewie.</span><span class="sxs-lookup"><span data-stu-id="cf5f3-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="cf5f3-110">Ten przykład generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="cf5f3-110">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
