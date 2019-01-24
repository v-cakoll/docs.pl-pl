---
title: 'Instrukcje: Określić, czy plik jest zestawem (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
ms.openlocfilehash: b8627c64398afdef00fde71121f870b337ac072f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520096"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="fc1ae-102">Instrukcje: Określić, czy plik jest zestawem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc1ae-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="fc1ae-103">Plik jest zestawem, tylko wtedy, gdy jest zarządzana i wpis zestawu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="fc1ae-104">Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz temat [manifestu zestawu](../../../../framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="fc1ae-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="fc1ae-105">Jak ręcznie określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="fc1ae-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="fc1ae-106">Rozpocznij [Ildasm.exe (dezasembler IL)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="fc1ae-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2.  <span data-ttu-id="fc1ae-107">Załaduj plik, który chcesz przetestować.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="fc1ae-108">Jeśli **ILDASM** raporty, że plik nie jest plikiem przenośny plik wykonywalny (PE), a następnie nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="fc1ae-109">Aby uzyskać więcej informacji, zobacz temat [jak: Wyświetlanie zawartości zestawu](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="fc1ae-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="fc1ae-110">Jak programowo określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="fc1ae-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="fc1ae-111">Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> jest metoda pełną ścieżkę i nazwę pliku, które testujesz.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="fc1ae-112">Jeśli <xref:System.BadImageFormatException> jest zgłaszany wyjątek, plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc1ae-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc1ae-113">Example</span></span>  
 <span data-ttu-id="fc1ae-114">W tym przykładzie testy bibliotekę DLL, aby zobaczyć, jeśli jest to zespół.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="fc1ae-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda ładuje plik testu i następnie zwalnia go po zostaną odczytane informacje.</span><span class="sxs-lookup"><span data-stu-id="fc1ae-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1ae-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc1ae-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="fc1ae-117">Pojęcia związane z programowaniem</span><span class="sxs-lookup"><span data-stu-id="fc1ae-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="fc1ae-118">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc1ae-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](index.md)
