---
title: 'Porady: Określanie, jeśli plik jest zestawem (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: ced41279e7e192d6d5bed53dbce7378395b32e6d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131623"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="b9e5f-102">Porady: Określanie, jeśli plik jest zestawem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9e5f-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="b9e5f-103">Plik jest zestawem, tylko wtedy, gdy jest zarządzana i wpis zestawu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="b9e5f-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="b9e5f-104">Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz temat [manifestu zestawu](../../../../framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b9e5f-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="b9e5f-105">Jak ręcznie określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="b9e5f-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="b9e5f-106">Rozpocznij [Ildasm.exe (dezasembler IL)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="b9e5f-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="b9e5f-107">Załaduj plik, który chcesz przetestować.</span><span class="sxs-lookup"><span data-stu-id="b9e5f-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="b9e5f-108">Jeśli **ILDASM** raporty, że plik nie jest plikiem przenośny plik wykonywalny (PE), a następnie nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="b9e5f-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="b9e5f-109">Aby uzyskać więcej informacji, zobacz temat [porady: wyświetlanie zawartości zestawu](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="b9e5f-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="b9e5f-110">Jak programowo określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="b9e5f-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="b9e5f-111">Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> jest metoda pełną ścieżkę i nazwę pliku, które testujesz.</span><span class="sxs-lookup"><span data-stu-id="b9e5f-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="b9e5f-112">Jeśli <xref:System.BadImageFormatException> jest zgłaszany wyjątek, plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="b9e5f-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9e5f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9e5f-113">Example</span></span>  
 <span data-ttu-id="b9e5f-114">W tym przykładzie testy bibliotekę DLL, aby zobaczyć, jeśli jest to zespół.</span><span class="sxs-lookup"><span data-stu-id="b9e5f-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
  
 <span data-ttu-id="b9e5f-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda ładuje plik testu i następnie zwalnia go po zostaną odczytane informacje.</span><span class="sxs-lookup"><span data-stu-id="b9e5f-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e5f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9e5f-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>  
- [<span data-ttu-id="b9e5f-117">Pojęcia związane z programowaniem</span><span class="sxs-lookup"><span data-stu-id="b9e5f-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
- [<span data-ttu-id="b9e5f-118">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9e5f-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
