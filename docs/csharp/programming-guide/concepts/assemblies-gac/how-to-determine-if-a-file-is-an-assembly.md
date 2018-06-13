---
title: 'Porady: Określanie, czy plik jest zestawem (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 0557f42d42e42606c3d1b2a2ad71bd797a159e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317986"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="45de9-102">Porady: Określanie, czy plik jest zestawem (C#)</span><span class="sxs-lookup"><span data-stu-id="45de9-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="45de9-103">Plik jest zestawem tylko wtedy, gdy jest zarządzana i wpis zestawu w metadanych.</span><span class="sxs-lookup"><span data-stu-id="45de9-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="45de9-104">Aby uzyskać więcej informacji dotyczących metadanych i zestawy, zobacz temat [manifestu zestawu](../../../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="45de9-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](../../../../../docs/framework/app-domains/assembly-manifest.md).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="45de9-105">Jak ręcznie ustalić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="45de9-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="45de9-106">Uruchom [Ildasm.exe (dezasembler IL)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="45de9-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="45de9-107">Załaduj plik, który chcesz przetestować.</span><span class="sxs-lookup"><span data-stu-id="45de9-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="45de9-108">Jeśli **narzędzia ILDASM** raporty, że plik nie jest plikiem przenośny plik wykonywalny (PE), a następnie nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="45de9-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="45de9-109">Aby uzyskać więcej informacji, zobacz temat [porady: wyświetlanie zawartości zestawu](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="45de9-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="45de9-110">Jak programowo ustalić, czy plik jest zestawem</span><span class="sxs-lookup"><span data-stu-id="45de9-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="45de9-111">Wywołanie <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> jest metoda pełną ścieżkę i nazwę pliku podczas testowania.</span><span class="sxs-lookup"><span data-stu-id="45de9-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="45de9-112">Jeśli <xref:System.BadImageFormatException> wyjątku, plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="45de9-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45de9-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="45de9-113">Example</span></span>  
 <span data-ttu-id="45de9-114">W tym przykładzie testy bibliotekę DLL, aby zobaczyć, czy jest on zestawem.</span><span class="sxs-lookup"><span data-stu-id="45de9-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```  
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
  
 <span data-ttu-id="45de9-115"><xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metody ładuje plik testu, a następnie zwalnia, gdy jest do odczytu informacji.</span><span class="sxs-lookup"><span data-stu-id="45de9-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45de9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45de9-116">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="45de9-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="45de9-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45de9-118">Zestawy i Globalna pamięć podręczna zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="45de9-118">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
