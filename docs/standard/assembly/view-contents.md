---
title: 'Instrukcje: wyświetlanie zawartości zestawu'
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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 40ed31bb2231775bb2b6eb24586e07c8b07a85bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053944"
---
# <a name="how-to-view-assembly-contents"></a>Instrukcje: wyświetlanie zawartości zestawu

Do wyświetlania informacji o języku pośrednim (MSIL) firmy Microsoft w pliku można użyć [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md) . Jeśli rozpatrywany plik jest zestawem, te informacje mogą obejmować atrybuty zestawu, a także odwołania do innych modułów i zestawów. Te informacje mogą być pomocne w ustaleniu, czy plik jest zestawem lub częścią zestawu oraz czy plik zawiera odwołania do innych modułów lub zestawów.  
  
Aby wyświetlić zawartość zestawu przy użyciu *Ildasm. exe*, w wierszu polecenia wpisz **Ildasm** \< *nazwę zestawu*, >. Na przykład następujące polecenie deasembleruje zestaw *Hello. exe* .  

```cmd
ildasm Hello.exe  
```  

Aby wyświetlić informacje o manifeście zestawu, kliknij dwukrotnie ikonę **manifestu** w oknie MSIL dezasembler.  
  
## <a name="example"></a>Przykład  

Poniższy przykład rozpoczyna się od podstawowego programu "Hello world". Po skompilowaniu programu należy użyć *Ildasm. exe* do rozbudowy zestawu *Hello. exe* i wyświetlić manifest zestawu.  

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
Imports System

Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

Uruchomienie polecenia *Ildasm. exe* w zestawie *Hello. exe* i dwukrotne kliknięcie ikony **manifestu** w oknie MSIL dezasembler generuje następujące dane wyjściowe:  

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
  
 W poniższej tabeli opisano każdą dyrektywę w manifeście zestawu zestawu *Hello. exe* użytego w tym przykładzie.  
  
|— Dyrektywa|Opis|  
|---------------|-----------------|  
|*Nazwa zestawu* **extern \< . Assembly** **>**|Określa inny zestaw, który zawiera elementy, do których odwołuje się bieżący moduł ( `mscorlib`w tym przykładzie).|  
|*token* **. \< PublicKeyToken** **>**|Określa token rzeczywistego klucza przywoływanego zestawu.|  
|*numer wersji* **. ver \<** **>**|Określa numer wersji przywoływanego zestawu.|  
|*Nazwa zestawu* **. Assembly \<** **>**|Określa nazwę zestawu.|  
|*wartość Int32* **algorytmu \< hash** **>**|Określa używany algorytm wyznaczania wartości skrótu.|  
|*numer wersji* **. ver \<** **>**|Określa numer wersji zestawu.|  
|*Nazwa pliku* **modułu \<** **>**|Określa nazwę modułów, które tworzą zestaw. W tym przykładzie zestaw składa się tylko z jednego pliku.|  
|**. podsystem \<**  — *wartość* **>**|Określa środowisko aplikacji wymagane dla programu. W tym przykładzie wartość 3 wskazuje, że ten plik wykonywalny jest uruchamiany z konsoli programu.|  
|**.corflags**|Obecnie zarezerwowane pole w metadanych.|  
  
 Manifest zestawu może zawierać wiele różnych dyrektyw, w zależności od zawartości zestawu. Aby uzyskać obszerną listę dyrektyw w manifeście zestawu, zapoznaj się z dokumentacją ECMA, szczególnie "partycja II: Definicja i semantyka metadanych "i" partycja III: Zestaw instrukcji CIL ". Dokumentacja jest dostępna w trybie online. Zobacz [standardy C# ECMA i Common Language Infrastructure](https://go.microsoft.com/fwlink/?LinkID=99212) w MSDN i [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w międzynarodowej witrynie internetowej ECMA.  
  
## <a name="see-also"></a>Zobacz także

- [Domeny aplikacji i zestawy](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Domeny aplikacji i zestawy Tematy porad](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (dezasembler IL)](../../framework/tools/ildasm-exe-il-disassembler.md)
