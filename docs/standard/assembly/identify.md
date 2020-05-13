---
title: 'Instrukcje: ustalanie, czy plik jest zestawem'
description: W tym artykule opisano, jak określić, czy plik jest zestawem .NET, zarówno ręcznie, jak i programowo.
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: fb1bcfa50ec380f10ab67cc47331f91dc3e4b32d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380146"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="148dd-103">Instrukcje: ustalanie, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="148dd-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="148dd-104">Plik jest zestawem, jeśli i tylko wtedy, gdy jest zarządzany, i zawiera wpis zestawu w jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="148dd-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="148dd-105">Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz [manifest zestawu](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="148dd-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="148dd-106">Jak ręcznie określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="148dd-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="148dd-107">Uruchom [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="148dd-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="148dd-108">Załaduj plik, który chcesz przetestować.</span><span class="sxs-lookup"><span data-stu-id="148dd-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="148dd-109">Jeśli **Ildasm** zgłasza, że plik nie jest przenośnym plikiem wykonywalnym (PE), to nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="148dd-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="148dd-110">Aby uzyskać więcej informacji, zobacz temat [jak: wyświetlanie zawartości zestawu](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="148dd-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="148dd-111">Jak programowo określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="148dd-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="148dd-112">Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodę, przekazując pełną ścieżkę pliku i nazwę testowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="148dd-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="148dd-113">Jeśli <xref:System.BadImageFormatException> wystąpi wyjątek, plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="148dd-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="148dd-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="148dd-114">Example</span></span>  
<span data-ttu-id="148dd-115">Ten przykład testuje DLL, aby sprawdzić, czy jest to zestaw.</span><span class="sxs-lookup"><span data-stu-id="148dd-115">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

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

<span data-ttu-id="148dd-116"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A>Metoda ładuje plik testowy, a następnie zwalnia go po odczytaniu informacji.</span><span class="sxs-lookup"><span data-stu-id="148dd-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148dd-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="148dd-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="148dd-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="148dd-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="148dd-119">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="148dd-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="148dd-120">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="148dd-120">Assemblies in .NET</span></span>](index.md)
