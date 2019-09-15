---
title: -moduleassemblyname — (C# opcja kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 7562c0609d61b2388f5063bc480a4dfc715155db
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970075"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname — (C# opcja kompilatora)
Określa zestaw, którego typy niepubliczne a. module mogą uzyskać dostęp.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
 `assembly_name`  
 Nazwa zestawu, którego typy niepubliczne mogą uzyskać dostęp do modułu.  
  
## <a name="remarks"></a>Uwagi  
 **-moduleassemblyname —** należy używać podczas kompilowania modułu. sieci i, gdy są spełnione następujące warunki:  
  
- Moduł. Webmusi mieć dostęp do niepublicznych typów w istniejącym zestawie.  
  
- Znasz nazwę zestawu, do którego zostanie skompilowany moduł.  
  
- Istniejący zestaw przydzieli znajomemu dostęp do zestawu, do którego zostanie skompilowany moduł.  
  
 Aby uzyskać więcej informacji na temat tworzenia modułu., zobacz [-target: module (C# opcje kompilatora)](./target-module-compiler-option.md).  
  
 Aby uzyskać więcej informacji o znajomych zestawach, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).  
  
 Ta opcja jest niedostępna w środowisku programistycznym; jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Ten przykład kompiluje zestaw z typem prywatnym i zapewnia znajomemu dostęp do zestawu o nazwie csman_an_assembly.  
  
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
 Ten przykład tworzy moduł. Service, który uzyskuje dostęp do niepublicznego typu w zestawie moduleassemblyname_1. dll. Wiedząc, że ten moduł. module zostanie skompilowany w zestawie o nazwie csman_an_assembly, możemy określić wartość **-moduleassemblyname —** , umożliwiając modułowi. servicedostęp do niepublicznych typów w zestawie, który udzielił znajomemu dostęp do zestawu csman_an_ hamulc.  
  
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
 Ten przykładowy kod kompiluje csman_an_assembly zestawu, który odwołuje się do wcześniej skompilowanego zestawu i modułu.  
  
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
  
**An_Internal_Class. test wywołany**

## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
