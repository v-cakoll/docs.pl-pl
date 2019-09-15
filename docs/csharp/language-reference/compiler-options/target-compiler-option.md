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
ms.openlocfilehash: 073660fa732c04cdc987af5617b894a277ebcc0f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970113"
---
# <a name="-target-c-compiler-options"></a>-Target (C# opcje kompilatora)
Opcja kompilatora **-Target** może być określona w jednej z czterech postaci:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Tworzenie pliku exe dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.  
  
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
  
 Manifest zestawu jest umieszczany w pierwszym pliku wyjściowym exe w kompilacji lub w pierwszej bibliotece DLL, jeśli nie ma pliku wyjściowego. exe. Na przykład w następującym wierszu polecenia manifest zostanie umieszczony w `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilator tworzy tylko jeden manifest zestawu na kompilację. Informacje o wszystkich plikach w kompilacji są umieszczane w manifeście zestawu. Wszystkie pliki wyjściowe z wyjątkiem plików utworzonych za pomocą **elementu-target: module** mogą zawierać manifest zestawu. W przypadku tworzenia wielu plików wyjściowych w wierszu polecenia można utworzyć tylko jeden manifest zestawu i musi on przejść do pierwszego pliku wyjściowego określonego w wierszu polecenia. Niezależnie od tego, jaki pierwszy plik wyjściowy jest ( **-target: exe**, **-target: winexe**, **-target: Library** lub **-target: module**), wszystkie inne pliki wyjściowe utworzone w tej samej kompilacji muszą być modułami ( **-target: module**).  
  
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
  
 Aby uzyskać więcej informacji o tym, jak można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (C# opcje kompilatora)](./subsystemversion-compiler-option.md)
