---
title: -target (Opcje kompilatora języka C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: ea5481810e629d911c4d5aba62e60c98d0783f34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644356"
---
# <a name="-target-c-compiler-options"></a>-target (Opcje kompilatora języka C#)
Opcja kompilatora **-target** można określić w jednym z czterech formularzy:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Aby utworzyć plik exe dla aplikacji ze Sklepu Windows 8.x.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Aby utworzyć plik exe.  
  
 [-target:library](./target-library-compiler-option.md)  
 Aby utworzyć bibliotekę kodu.  
  
 [-target:module](./target-module-compiler-option.md)  
 Aby utworzyć moduł.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Aby utworzyć program windowsowy.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Aby utworzyć pośredni plik .winmdobj.  
  
 O ile nie określisz **-target:module**, **-target** powoduje, że manifest zestawu .NET Framework ma zostać umieszczony w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [Zestawy w .NET](../../../standard/assembly/index.md) i [Common Attributes](../attributes/global.md).  
  
 Manifest zestawu jest umieszczany w pierwszym pliku wyjściowym exe w kompilacji lub w pierwszej dll, jeśli nie ma pliku wyjściowego .exe. Na przykład w następującym wierszu polecenia manifest `1.exe`zostanie umieszczony w:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilator tworzy tylko jeden manifest zestawu na kompilację. Informacje o wszystkich plikach w kompilacji są umieszczane w manifeście zestawu. Wszystkie pliki wyjściowe z wyjątkiem plików utworzonych za pomocą **-target:module** mogą zawierać manifest zestawu. Podczas tworzenia wielu plików wyjściowych w wierszu polecenia można utworzyć tylko jeden manifest zestawu i musi on przejść do pierwszego pliku wyjściowego określonego w wierszu polecenia. Bez względu na to, jaki jest pierwszy plik wyjściowy (**-target:exe**, **-target:winexe**, **-target:library** lub **-target:module**), wszelkie inne pliki wyjściowe wyprodukowane w tej samej kompilacji muszą być modułami (**-target:module**).  
  
 Jeśli utworzysz zestaw, można wskazać, że całość lub część <xref:System.CLSCompliantAttribute> kodu jest cls zgodne z atrybutem.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Aby uzyskać więcej informacji na temat programowania <xref:VSLangProj80.ProjectProperties3.OutputType%2A>ustawiania tej opcji kompilatora, zobacz .  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (Opcje kompilatora języka C#)](./subsystemversion-compiler-option.md)
