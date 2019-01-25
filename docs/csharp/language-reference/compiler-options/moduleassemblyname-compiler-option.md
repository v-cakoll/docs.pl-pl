---
title: -moduleassemblyname — (opcją kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: bc1bc1376271b3a01d9b720dd85f812ea55cf34c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665048"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname — (opcją kompilatora C#)
Określa, których typy bez publicznego .netmodule mogą uzyskiwać dostęp do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
 `assembly_name`  
 Nazwa zestawu, którego niepublicznych typy .netmodule mogą uzyskiwać dostęp.  
  
## <a name="remarks"></a>Uwagi  
 **-moduleassemblyname** należy używać podczas tworzenia modułu .netmodule, a w przypadku, gdy są spełnione następujące warunki:  
  
-   .netmodule musi mieć dostęp do typów niepublicznych w istniejącego zestawu.  
  
-   Znasz nazwę zestawu, do którego zostanie utworzona .netmodule.  
  
-   Istniejący zestaw przyznał prawa dostępu do zestawu friend do zestawu, do którego zostanie utworzona .netmodule.  
  
 Aby uzyskać więcej informacji na temat budowania .netmodule zobacz [-target: module (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Aby uzyskać więcej informacji na temat przyjaznych zestawów, zobacz [przyjaznych zestawów](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
 Ta opcja nie jest dostępne z poziomu środowiska programistycznego; jest on dostępny tylko wtedy, podczas kompilowania z wiersza polecenia.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Ten przykład tworzy zestaw o prywatny typ i daje dostęp do zestawu friend do zestawu o nazwie csman_an_assembly.  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład tworzy .netmodule, który uzyskuje dostęp do typu niepublicznych w moduleassemblyname_1.dll zestawu. Wiadomo, że tego modułu .netmodule zostanie skompilowany w zestawie o nazwie csman_an_assembly, można określić **- moduleassemblyname**, dzięki czemu netmodule można uzyskiwać dostęp do typów niepublicznych w zestawie, który przyznał przyjaznego zestawu dostęp do csman_an_assembly.  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a>Przykład  
 Ten przykładowy kod tworzy csman_an_assembly zestawu, odwołania do zestawu wcześniej skompilowana i .netmodule.  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
**An_Internal_Class.test o nazwie**

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
