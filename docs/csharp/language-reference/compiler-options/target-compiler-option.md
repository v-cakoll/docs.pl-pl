---
title: -target (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: a337ecbc614ff40eda42fc5263dbb52aa92b905f
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339594"
---
# <a name="-target-c-compiler-options"></a>-target (opcje kompilatora C#)
**-Target** — opcja kompilatora można określić w jednej z czterech form:  
  
 [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Aby utworzyć plik .exe [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.  
  
 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Aby utworzyć plik .exe.  
  
 [-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Aby utworzyć bibliotekę kodu.  
  
 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Aby utworzyć moduł.  
  
 [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Aby utworzyć Windows program.  
  
 [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Aby utworzyć plik pośredni .winmdobj.  
  
 Chyba że określisz **-target: module**, **-target** powoduje, że manifest zestawu .NET Framework, należy umieścić w pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [zestawów w środowisko uruchomieniowe języka wspólnego](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) i [wspólne atrybuty](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Manifest zestawu jest umieszczany w pierwszym pliku wyjściowego .exe w kompilacji lub w pierwszym pliku DLL, jeśli nie ma żadnego pliku wyjściowego .exe. Na przykład, w wierszu polecenia następujące manifestu zostaną umieszczone w `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilator tworzy tylko jeden manifest zestawu kompilacji. Informacje o wszystkich plikach w zestawieniu jest umieszczany w manifeście zestawu. Wszystkie pliki, z wyjątkiem tych utworzonych za pomocą wyjściowe **-target: module** może zawierać manifest zestawu. Podczas produkowania wiele plików wyjściowych w wierszu polecenia, można utworzyć tylko jedną manifestu dla aplikacji i musi przejść do pierwszego pliku wyjściowego, określone w wierszu polecenia. Niezależnie od tego, jakie pierwszy plik wyjściowy jest (**-target: exe**, **-target: winexe**, **-target: library** lub **-target: module**) wszystkie inne pliki wyjściowe utworzone w tej samej kompilacji musi być modułów (**-target: module**).  
  
 Jeśli utworzysz zestaw, można wskazać, że całość lub część kodu jest zgodne ze specyfikacją CLS <xref:System.CLSCompliantAttribute> atrybutu.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Aby uzyskać więcej informacji na temat programowego ustawiania tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
- [-subsystemversion (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
