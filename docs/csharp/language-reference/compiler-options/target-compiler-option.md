---
title: -Target (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 80cec001b27000e71b74f380a0f33e30602c01af
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86473912"
---
# <a name="-target-c-compiler-options"></a>-Target (opcje kompilatora C#)
Opcję kompilatora **-Target** można określić w jednej z następujących form:  
  
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
  
 O ile nie określono **elementu-target: module**, **-Target** powoduje, że manifest zestawu .NET Framework zostanie umieszczony w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [zestawy w programie .NET](../../../standard/assembly/index.md) i [wspólne atrybuty](../attributes/global.md).  
  
 Manifest zestawu jest umieszczany w pierwszym pliku wyjściowym exe w kompilacji lub w pierwszej bibliotece DLL, jeśli nie ma pliku wyjściowego. exe. Na przykład w następującym wierszu polecenia manifest zostanie umieszczony w `1.exe` :  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilator tworzy tylko jeden manifest zestawu na kompilację. Informacje o wszystkich plikach w kompilacji są umieszczane w manifeście zestawu. Wszystkie pliki wyjściowe z wyjątkiem plików utworzonych za pomocą **elementu-target: module** mogą zawierać manifest zestawu. W przypadku tworzenia wielu plików wyjściowych w wierszu polecenia można utworzyć tylko jeden manifest zestawu i musi on przejść do pierwszego pliku wyjściowego określonego w wierszu polecenia. Niezależnie od tego, jaki pierwszy plik wyjściowy jest (**-target: exe**, **-target: winexe**, **-target: Library** lub **-target: module**), wszystkie inne pliki wyjściowe utworzone w tej samej kompilacji muszą być modułami (**-target: module**).  
  
 W przypadku utworzenia zestawu można wskazać, że całość lub część kodu jest zgodna ze specyfikacją CLS z <xref:System.CLSCompliantAttribute> atrybutem.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Aby uzyskać więcej informacji o tym, jak można programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (opcje kompilatora C#)](./subsystemversion-compiler-option.md)
