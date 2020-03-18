---
title: -moduleassemblyname (Opcja kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 1477eeb0f2e16e18cb86009739bc8e7d9dee2ac0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173721"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (Opcja kompilatora C#)
Określa zestaw, do którego niepubliczne typy .netmodule mogą uzyskać dostęp.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
 `assembly_name`  
 Nazwa zestawu, którego niepubliczne typy .netmodule można uzyskać dostęp.  
  
## <a name="remarks"></a>Uwagi  
 **-moduleassemblyname** należy używać podczas tworzenia .netmodule i tam, gdzie spełnione są następujące warunki:  
  
- Moduł .netmodule wymaga dostępu do typów niepublicznych w istniejącym zestawie.  
  
- Znasz nazwę zestawu, w którym zostanie utworzony moduł .netmodule.  
  
- Istniejący zestaw przyznał zestawowi znajomych dostęp do zestawu, w którym zostanie utworzony moduł .netmodule.  
  
 Aby uzyskać więcej informacji na temat tworzenia .netmodule, zobacz [-target:module (Opcje kompilatora C#)](./target-module-compiler-option.md).  
  
 Aby uzyskać więcej informacji na temat zgromadzeń znajomych, zobacz [Zestawy znajomych](../../../standard/assembly/friend.md).  
  
 Ta opcja nie jest dostępna w środowisku programistycznym; jest dostępna tylko podczas kompilowania z wiersza polecenia.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Ten przykład tworzy zestaw z typem prywatnym i który daje dostęp do zestawu znajomego do zestawu o nazwie csman_an_assembly.  
  
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
 Ten przykład tworzy .netmodule, który uzyskuje dostęp do typu niepublicznego w zestawie moduleassemblyname_1.dll. Wiedząc, że ten .netmodule zostanie wbudowany w zestaw o nazwie csman_an_assembly, możemy określić **-moduleassemblyname,** umożliwiając modułowi .netmoduł dostęp do typów niepublicznych w zestawie, który przyznał dostęp do zestawu znajomych do csman_an_assembly.  
  
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
 Ten przykładowy kod tworzy csman_an_assembly zestawu, odwołując się do wcześniej utworzonego zestawu i .netmodule.  
  
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
  
**An_Internal_Class.Test o nazwie**

## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
