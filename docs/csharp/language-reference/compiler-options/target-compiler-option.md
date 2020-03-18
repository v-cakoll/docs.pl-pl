---
title: -target (Opcje kompilatora C#)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204515"
---
# <a name="-target-c-compiler-options"></a>-target (Opcje kompilatora C#)
Opcja **-target** kompilator akcesora można określić w jednej z czterech form:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Aby utworzyć plik exe dla aplikacji ze Sklepu Windows 8.x.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Aby utworzyć plik exe.  
  
 [-target:library](./target-library-compiler-option.md)  
 Aby utworzyć bibliotekę kodu.  
  
 [-target:module](./target-module-compiler-option.md)  
 Aby utworzyć moduł.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Aby utworzyć program systemu Windows.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Aby utworzyć pośredni plik .winmdobj.  
  
 Jeśli nie określisz **-target:module**, **-target** powoduje, że manifest zestawu .NET Framework ma być umieszczony w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [Zestawy w .NET](../../../standard/assembly/index.md) i [atrybuty wspólne](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Manifest zestawu jest umieszczany w pierwszym pliku wyjściowym .exe w kompilacji lub w pierwszej dll, jeśli nie ma pliku wyjściowego .exe. Na przykład w następującym wierszu polecenia manifest `1.exe`zostanie umieszczony w :  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilator tworzy tylko jeden manifest zestawu na kompilację. Informacje o wszystkich plikach w kompilacji jest umieszczany w manifeście zestawu. Wszystkie pliki wyjściowe z wyjątkiem tych utworzonych za pomocą **-target:module** może zawierać manifest zestawu. Podczas tworzenia wielu plików wyjściowych w wierszu polecenia można utworzyć tylko jeden manifest zestawu i musi przejść do pierwszego pliku wyjściowego określonego w wierszu polecenia. Bez względu na to, jaki jest pierwszy plik wyjściowy (**-target:exe**, **-target:winexe**, **-target:library** lub **-target:module),** wszelkie inne pliki wyjściowe wyprodukowane w tej samej kompilacji muszą być modułami (**-target:module**).  
  
 Jeśli utworzysz zestaw, można wskazać, że cały lub część <xref:System.CLSCompliantAttribute> kodu jest zgodny z cls z atrybutem.  
  
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

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (Opcje kompilatora C#)](./subsystemversion-compiler-option.md)
