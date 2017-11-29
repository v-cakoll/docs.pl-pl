---
title: -moduleassemblyname (opcja kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8ebd6f7498adead4586c9e90ec58ca8efe81aaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname-c-compiler-option"></a>/moduleassemblyname (opcja kompilatora C#)
Określa, których typy niepublicznych modułu .netmodule mogą uzyskiwać dostęp do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
 `assembly_name`  
 Nazwa zestawu, którego niepublicznych typy modułu .netmodule mogą uzyskać dostęp.  
  
## <a name="remarks"></a>Uwagi  
 **/ moduleassemblyname** powinien być używany podczas kompilowania modułu .netmodule, a w przypadku, gdy są spełnione następujące warunki:  
  
-   Modułu .netmodule musi mieć dostęp do typów niepublicznych w istniejącego zestawu.  
  
-   Znasz nazwę zestawu, do którego zostaną skompilowane modułu .netmodule.  
  
-   Istniejącego zestawu udzielił dostęp do przyjaznego zestawu do zestawu, do którego zostaną skompilowane modułu .netmodule.  
  
 Aby uzyskać więcej informacji dotyczących tworzenia modułu .netmodule, zobacz [/target: module (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Aby uzyskać więcej informacji na przyjaznych zestawów, zobacz [przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
 Ta opcja nie jest dostępne w środowisku programistycznym; jest on dostępny tylko wtedy, podczas kompilowania z wiersza polecenia.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Ten przykład tworzy zestaw o prywatny typ i zapewniającą dostęp do przyjaznego zestawu do zestawu o nazwie csman_an_assembly.  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: /target:library  
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
 Ten przykład tworzy modułu .netmodule, który uzyskuje dostęp do niepublicznego typu w moduleassemblyname_1.dll zestawu. Wiadomo, że tego modułu .netmodule będzie można wbudować do zestawu o nazwie csman_an_assembly, można określić **/moduleassemblyname**, dzięki czemu modułu .netmodule do niepublicznego typów w zestawie, który został udzielony przyjaznego zestawu dostęp do csman_an_assembly.  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a>Przykład  
 Ten przykładowy kod tworzy csman_an_assembly zestawu, odwołuje się do wcześniej skompilowany zestaw i modułu .netmodule.  
  
```csharp  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
 **An_Internal_Class.test o nazwie**  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
