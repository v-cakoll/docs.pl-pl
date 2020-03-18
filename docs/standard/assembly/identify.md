---
title: 'Jak: Określić, czy plik jest złożeniem'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1d66c0c166724f195a3cafd9bcbe3c7414c08ebb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159510"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Jak: Określić, czy plik jest złożeniem

Plik jest zestawem, jeśli i tylko wtedy, gdy jest zarządzany i zawiera wpis zestawu w swoich metadanych. Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz [Manifest zestawu](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ręcznie określić, czy plik jest złożeniem  
  
1. Uruchom [program Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Załaduj plik, który chcesz przetestować.  
  
3. Jeśli **ILDASM** zgłasza, że plik nie jest przenośnyplik wykonywalny (PE), to nie jest to zestaw. Aby uzyskać więcej informacji, zobacz temat [Jak: Wyświetlanie zawartości zestawu](view-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programowo określić, czy plik jest złożeniem  
  
1. Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodę, przekazując pełną ścieżkę pliku i nazwę testowego pliku.  
  
2. Jeśli <xref:System.BadImageFormatException> wyjątek zostanie zgłoszony, plik nie jest zestawem.  
  
## <a name="example"></a>Przykład  
W tym przykładzie testów dll, aby sprawdzić, czy jest to zestaw.  

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

Metoda <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> ładuje plik testowy, a następnie zwalnia go po odczytaniu informacji.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection.AssemblyName>
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](index.md)
