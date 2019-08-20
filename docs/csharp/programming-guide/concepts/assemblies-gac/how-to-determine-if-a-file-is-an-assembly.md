---
title: 'Instrukcje: Ustal, czy plik jest zestawem (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 803159eed25a7785b1a2b4433e6950fa65e0a734
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595865"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="bf8f7-102">Instrukcje: Ustal, czy plik jest zestawem (C#)</span><span class="sxs-lookup"><span data-stu-id="bf8f7-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="bf8f7-103">Plik jest zestawem, jeśli i tylko wtedy, gdy jest zarządzany, i zawiera wpis zestawu w jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="bf8f7-104">Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz [manifest zestawu](../../../../framework/app-domains/assembly-manifest.md)tematów.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="bf8f7-105">Jak ręcznie określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="bf8f7-105">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="bf8f7-106">Uruchom [Ildasm. exe (Il dezasembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="bf8f7-106">Start the [Ildasm.exe (IL Disassembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="bf8f7-107">Załaduj plik, który chcesz przetestować.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-107">Load the file you wish to test.</span></span>  
  
3. <span data-ttu-id="bf8f7-108">Jeśli **Ildasm** zgłasza, że plik nie jest przenośnym plikiem wykonywalnym (PE), to nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="bf8f7-109">Więcej informacji można znaleźć w temacie [How to: Wyświetl zawartość](../../../../framework/app-domains/how-to-view-assembly-contents.md)zestawu.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="bf8f7-110">Jak programowo określić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="bf8f7-110">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="bf8f7-111">Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> metodę, przekazując pełną ścieżkę pliku i nazwę testowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="bf8f7-112"><xref:System.BadImageFormatException> Jeśli wystąpi wyjątek, plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf8f7-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf8f7-113">Example</span></span>  
 <span data-ttu-id="bf8f7-114">Ten przykład testuje DLL, aby sprawdzić, czy jest to zestaw.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
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
  
 <span data-ttu-id="bf8f7-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda ładuje plik testowy, a następnie zwalnia go po odczytaniu informacji.</span><span class="sxs-lookup"><span data-stu-id="bf8f7-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf8f7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf8f7-116">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="bf8f7-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bf8f7-117">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="bf8f7-118">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="bf8f7-118">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
