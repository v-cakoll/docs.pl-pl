---
title: 'Instrukcje: Ustal, czy plik jest zestawem'
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: f9bff86ac559e40136ed016b862eef8ba0863ce3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973223"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a>Instrukcje: Ustal, czy plik jest zestawem

Plik jest zestawem, jeśli i tylko wtedy, gdy jest zarządzany, i zawiera wpis zestawu w jego metadanych. Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz [manifest zestawu](manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ręcznie określić, czy plik jest zestawem  
  
1. Uruchom [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Załaduj plik, który chcesz przetestować.  
  
3. Jeśli **Ildasm** zgłasza, że plik nie jest przenośnym plikiem wykonywalnym (PE), to nie jest zestawem. Więcej informacji można znaleźć w temacie [How to: Wyświetl zawartość](view-contents.md)zestawu.  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programowo określić, czy plik jest zestawem  
  
1. Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> metodę, przekazując pełną ścieżkę pliku i nazwę testowanego pliku.  
  
2. <xref:System.BadImageFormatException> Jeśli wystąpi wyjątek, plik nie jest zestawem.  
  
## <a name="example"></a>Przykład  
Ten przykład testuje DLL, aby sprawdzić, czy jest to zestaw.  

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
 
<xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda ładuje plik testowy, a następnie zwalnia go po odczytaniu informacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.AssemblyName>
- [C#Przewodnik programowania](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](index.md)
