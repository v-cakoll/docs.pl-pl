---
title: 'Jak: Wyświetlanie zawartości zestawu'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187387"
---
# <a name="how-to-view-assembly-contents"></a>Jak: Wyświetlanie zawartości zestawu

Za pomocą [programu Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) można wyświetlić informacje o języku pośrednim firmy Microsoft (MSIL) w pliku. Jeśli badany plik jest zestawem, te informacje mogą zawierać atrybuty zestawu i odwołania do innych modułów i zestawów. Te informacje mogą być pomocne w określeniu, czy plik jest zestawem lub częścią zestawu i czy plik ma odwołania do innych modułów lub zestawów.

Aby wyświetlić zawartość złożenia przy użyciu *programu Ildasm.exe,* wprowadź **nazwę zestawu ildasm \<>** w wierszu polecenia. Na przykład następujące polecenie demontuje zestaw *Hello.exe.*

```cmd
ildasm Hello.exe
```

Aby wyświetlić informacje manifestu zestawu, kliknij dwukrotnie ikonę **manifestu** w oknie Disaser MSIL.

## <a name="example"></a>Przykład

Poniższy przykład rozpoczyna się od podstawowego programu "Hello World". Po skompilowaniu programu należy użyć *programu Ildasm.exe* do demontażu zestawu *Hello.exe* i wyświetl manifest zestawu.

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

Uruchamianie polecenia *ildasm.exe* w zestawie *Hello.exe* i dwukrotne kliknięcie **ikony Manifestu** w oknie Disassembler MSIL daje następujące dane wyjściowe:

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

W poniższej tabeli opisano każdą dyrektywę w manifeście zestawu *Hello.exe* użytym w przykładzie:

|Dyrektywy|Opis|
|---------------|-----------------|
|**Nazwa złożenia .assembly extern \<>**|Określa inny zestaw, który zawiera elementy, do których `mscorlib`odwołuje się bieżący moduł (w tym przykładzie).|
|**token \<tokenu .publickey token>**|Określa token rzeczywistego klucza zestawu, do którego istnieje odwołanie.|
|**Numer \<wersji .ver>**|Określa numer wersji zestawu, do którego istnieje odwołanie.|
|**Nazwa \<zestawu .>**|Określa nazwę zestawu.|
|**Wartość .hash algorytm \<int32>**|Określa algorytm mieszania używane.|
|**Numer \<wersji .ver>**|Określa numer wersji zestawu.|
|**Nazwa \<pliku .module>**|Określa nazwę modułów, które tworzą złożenie. W tym przykładzie zestaw składa się tylko z jednego pliku.|
|**Wartość .subsystem \<>**|Określa środowisko aplikacji wymagane dla programu. W tym przykładzie wartość 3 wskazuje, że ten plik wykonywalny jest uruchamiany z konsoli.|
|**.corflags (corflags)**|Obecnie zarezerwowane pole w metadanych.|

Manifest zestawu może zawierać szereg różnych dyrektyw, w zależności od zawartości zestawu. Obszerna lista dyrektyw w manifeście zestawu znajduje się w dokumentacji Ecma, szczególnie "Partycja II: Definicja metadanych i semantyka" i "Partycja III: Zestaw instrukcji CIL":

- [Normy ECMA C# i common language infrastructure](../components.md#applicable-standards)
- [Standard ECMA-335 - Wspólna infrastruktura językowa (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>Zobacz też

- [Domeny i zestawy aplikacji](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Tematy inkluzywne domen aplikacji i zestawów](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (dezasembler IL)](../../framework/tools/ildasm-exe-il-disassembler.md)
