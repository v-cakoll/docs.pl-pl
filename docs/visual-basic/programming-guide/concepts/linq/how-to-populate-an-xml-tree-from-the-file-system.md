---
title: 'Porady: wypełnianie drzewo XML z systemu plików (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 34eec79e-7945-4ba8-9f74-d05bb8ec67f6
ms.openlocfilehash: 158a6c5c6734f0aa11e22b5cbea35c960c7a1c40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642563"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-visual-basic"></a><span data-ttu-id="25afb-102">Porady: wypełnianie drzewo XML z systemu plików (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25afb-102">How to: Populate an XML Tree from the File System (Visual Basic)</span></span>
<span data-ttu-id="25afb-103">Typowe i przydatne aplikacji drzew XML jest jako magazynu danych hierarchiczna nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="25afb-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="25afb-104">Można wypełnić drzewo XML z danymi hierarchicznymi i jego zapytania, przekształcać je i w razie potrzeby go serializować.</span><span class="sxs-lookup"><span data-stu-id="25afb-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="25afb-105">W tym scenariuszu użycia nie są wiele semantyki określonego XML, takie jak obszary nazw i zachowanie biały znak, ważne.</span><span class="sxs-lookup"><span data-stu-id="25afb-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="25afb-106">Zamiast tego drzewa XML jest używany jako mały w pamięci, hierarchiczna baza danych jednego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25afb-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25afb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="25afb-107">Example</span></span>  
 <span data-ttu-id="25afb-108">Poniższy przykład powoduje wypełnienie drzewo XML z lokalnego systemu plików za pomocą rekursji.</span><span class="sxs-lookup"><span data-stu-id="25afb-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="25afb-109">Zapytanie drzewa obliczanie łączny rozmiar wszystkich plików w drzewie.</span><span class="sxs-lookup"><span data-stu-id="25afb-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```vb  
Module Module1  
    Function CreateFileSystemXmlTree(ByVal source As String) As XElement  
        Dim di As DirectoryInfo = New DirectoryInfo(source)  
        Return <Dir Name=<%= di.Name %>>  
                   <%= From d In Directory.GetDirectories(source) _  
                       Select CreateFileSystemXmlTree(d) %>  
                   <%= From fi In di.GetFiles() _  
                       Select <File>  
                                  <Name><%= fi.Name %></Name>  
                                  <Length><%= fi.Length %></Length>  
                              </File> %>  
               </Dir>  
    End Function  
  
    Sub Main()  
        Dim fileSystemTree As XElement = CreateFileSystemXmlTree("C:/Tmp")  
        Console.WriteLine(fileSystemTree)  
        Console.WriteLine("------")  
        Dim totalFileSize As Long = _  
            ( _  
                From f In fileSystemTree...<File> _  
                Select CLng(f.<Length>(0)) _  
            ).Sum()  
        Console.WriteLine("Total File Size:{0}", totalFileSize)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="25afb-110">W tym przykładzie generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="25afb-110">This example produces output similar to the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25afb-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25afb-111">See Also</span></span>  
 [<span data-ttu-id="25afb-112">Zaawansowane techniki zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25afb-112">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
