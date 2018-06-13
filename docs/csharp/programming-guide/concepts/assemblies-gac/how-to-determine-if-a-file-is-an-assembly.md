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
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Porady: Określanie, czy plik jest zestawem (C#)
Plik jest zestawem tylko wtedy, gdy jest zarządzana i wpis zestawu w metadanych. Aby uzyskać więcej informacji dotyczących metadanych i zestawy, zobacz temat [manifestu zestawu](../../../../../docs/framework/app-domains/assembly-manifest.md).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ręcznie ustalić, czy plik jest zestawem  
  
1.  Uruchom [Ildasm.exe (dezasembler IL)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Załaduj plik, który chcesz przetestować.  
  
3.  Jeśli **narzędzia ILDASM** raporty, że plik nie jest plikiem przenośny plik wykonywalny (PE), a następnie nie jest zestawem. Aby uzyskać więcej informacji, zobacz temat [porady: wyświetlanie zawartości zestawu](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programowo ustalić, czy plik jest zestawem  
  
1.  Wywołanie <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> jest metoda pełną ścieżkę i nazwę pliku podczas testowania.  
  
2.  Jeśli <xref:System.BadImageFormatException> wyjątku, plik nie jest zestawem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie testy bibliotekę DLL, aby zobaczyć, czy jest on zestawem.  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metody ładuje plik testu, a następnie zwalnia, gdy jest do odczytu informacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Reflection.AssemblyName>  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
