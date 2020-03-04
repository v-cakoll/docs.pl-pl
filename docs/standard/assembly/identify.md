---
title: 'Instrukcje: ustalanie, czy plik jest zestawem'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1d66c0c166724f195a3cafd9bcbe3c7414c08ebb
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159510"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="dd679-102">Instrukcje: ustalanie, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="dd679-102">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="dd679-103">Plik jest zestawem, jeśli i tylko wtedy, gdy jest zarządzany, i zawiera wpis zestawu w jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="dd679-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="dd679-104">Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz [manifest zestawu](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="dd679-104">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="dd679-105">Jak ręcznie określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="dd679-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="dd679-106">Uruchom [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="dd679-106">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="dd679-107">Załaduj plik, który chcesz przetestować.</span><span class="sxs-lookup"><span data-stu-id="dd679-107">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="dd679-108">Jeśli **Ildasm** zgłasza, że plik nie jest przenośnym plikiem wykonywalnym (PE), to nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="dd679-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="dd679-109">Aby uzyskać więcej informacji, zobacz temat [jak: wyświetlanie zawartości zestawu](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="dd679-109">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="dd679-110">Jak programowo określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="dd679-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="dd679-111">Wywołaj metodę <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>, przekazując pełną ścieżkę pliku i nazwę testowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="dd679-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="dd679-112">Jeśli zostanie zgłoszony wyjątek <xref:System.BadImageFormatException>, plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="dd679-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd679-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd679-113">Example</span></span>  
<span data-ttu-id="dd679-114">Ten przykład testuje DLL, aby sprawdzić, czy jest to zestaw.</span><span class="sxs-lookup"><span data-stu-id="dd679-114">This example tests a DLL to see if it is an assembly.</span></span>  

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

<span data-ttu-id="dd679-115">Metoda <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> ładuje plik testowy, a następnie zwalnia go po odczytaniu informacji.</span><span class="sxs-lookup"><span data-stu-id="dd679-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd679-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd679-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="dd679-117">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="dd679-117">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="dd679-118">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd679-118">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="dd679-119">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="dd679-119">Assemblies in .NET</span></span>](index.md)
