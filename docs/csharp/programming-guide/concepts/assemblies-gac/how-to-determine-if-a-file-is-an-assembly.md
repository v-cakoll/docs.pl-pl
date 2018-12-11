---
title: 'Instrukcje: Określić, czy plik jest zestawem (C#)'
ms.date: 07/20/2015
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
ms.openlocfilehash: 0cf9258aa4a5a1a633ee0bb04808d384de8f48d0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125538"
---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Instrukcje: Określić, czy plik jest zestawem (C#)
Plik jest zestawem, tylko wtedy, gdy jest zarządzana i wpis zestawu w metadanych. Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz temat [manifestu zestawu](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ręcznie określić, czy plik jest zestawem  
  
1.  Rozpocznij [Ildasm.exe (dezasembler IL)](../../../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2.  Załaduj plik, który chcesz przetestować.  
  
3.  Jeśli **ILDASM** raporty, że plik nie jest plikiem przenośny plik wykonywalny (PE), a następnie nie jest zestawem. Aby uzyskać więcej informacji, zobacz temat [jak: Wyświetlanie zawartości zestawu](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programowo określić, czy plik jest zestawem  
  
1.  Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> jest metoda pełną ścieżkę i nazwę pliku, które testujesz.  
  
2.  Jeśli <xref:System.BadImageFormatException> jest zgłaszany wyjątek, plik nie jest zestawem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie testy bibliotekę DLL, aby zobaczyć, jeśli jest to zespół.  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda ładuje plik testu i następnie zwalnia go po zostaną odczytane informacje.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.AssemblyName>  
- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
- [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
