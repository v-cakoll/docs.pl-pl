---
title: -Target (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204515"
---
# <a name="-target-c-compiler-options"></a>-Target (C# opcje kompilatora)
Opcja kompilatora **-Target** może być określona w jednej z czterech postaci:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Aby utworzyć plik exe dla aplikacji ze sklepu Windows 8. x.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Do utworzenia pliku. exe.  
  
 [-target:library](./target-library-compiler-option.md)  
 Aby utworzyć bibliotekę kodu.  
  
 [-target:module](./target-module-compiler-option.md)  
 Do utworzenia modułu.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Do utworzenia programu systemu Windows.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Aby utworzyć pośredni plik. winmdobj.  
  
 O ile nie określono **elementu-target: module**, **-Target** powoduje, że manifest zestawu .NET Framework zostanie umieszczony w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [zestawy w programie .NET](../../../standard/assembly/index.md) i [wspólne atrybuty](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Manifest zestawu jest umieszczany w pierwszym pliku wyjściowym exe w kompilacji lub w pierwszej bibliotece DLL, jeśli nie ma pliku wyjściowego. exe. Na przykład w poniższym wierszu polecenia manifest zostanie umieszczony w `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilator tworzy tylko jeden manifest zestawu na kompilację. Informacje o wszystkich plikach w kompilacji są umieszczane w manifeście zestawu. Wszystkie pliki wyjściowe z wyjątkiem plików utworzonych za pomocą **elementu-target: module** mogą zawierać manifest zestawu. W przypadku tworzenia wielu plików wyjściowych w wierszu polecenia można utworzyć tylko jeden manifest zestawu i musi on przejść do pierwszego pliku wyjściowego określonego w wierszu polecenia. Niezależnie od tego, jaki pierwszy plik wyjściowy jest ( **-target: exe**, **-target: winexe**, **-target: Library** lub **-target: module**), wszystkie inne pliki wyjściowe utworzone w tej samej kompilacji muszą być modułami ( **-target: module**).  
  
 W przypadku utworzenia zestawu można wskazać, że całość lub część kodu jest zgodna ze specyfikacją CLS z atrybutem <xref:System.CLSCompliantAttribute>.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Aby uzyskać więcej informacji o tym, jak można programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (C# opcje kompilatora)](./subsystemversion-compiler-option.md)
