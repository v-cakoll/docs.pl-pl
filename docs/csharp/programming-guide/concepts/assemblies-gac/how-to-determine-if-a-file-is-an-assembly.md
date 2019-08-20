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
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Instrukcje: Ustal, czy plik jest zestawem (C#)
Plik jest zestawem, jeśli i tylko wtedy, gdy jest zarządzany, i zawiera wpis zestawu w jego metadanych. Aby uzyskać więcej informacji na temat zestawów i metadanych, zobacz [manifest zestawu](../../../../framework/app-domains/assembly-manifest.md)tematów.  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Jak ręcznie określić, czy plik jest zestawem  
  
1. Uruchom [Ildasm. exe (Il dezasembler)](../../../../framework/tools/ildasm-exe-il-disassembler.md).  
  
2. Załaduj plik, który chcesz przetestować.  
  
3. Jeśli **Ildasm** zgłasza, że plik nie jest przenośnym plikiem wykonywalnym (PE), to nie jest zestawem. Więcej informacji można znaleźć w temacie [How to: Wyświetl zawartość](../../../../framework/app-domains/how-to-view-assembly-contents.md)zestawu.  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Jak programowo określić, czy plik jest zestawem  
  
1. Wywołaj <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> metodę, przekazując pełną ścieżkę pliku i nazwę testowanego pliku.  
  
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
  
 <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> Metoda ładuje plik testowy, a następnie zwalnia go po odczytaniu informacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.AssemblyName>
- [Przewodnik programowania w języku C#](../../index.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
