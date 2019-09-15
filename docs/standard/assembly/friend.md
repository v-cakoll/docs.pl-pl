---
title: Przyjazne zestawy
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 6387e93bcd4efeec57ada9228dcaf015d053dbf7
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973237"
---
# <a name="friend-assemblies"></a>Przyjazne zestawy

*Zestaw zaprzyjaźniony* jest zestawem, który może uzyskiwać dostęp do typów iC#elementów [wewnętrznych](../../csharp/language-reference/keywords/internal.md) () lub [zaprzyjaźnionych](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) innego zestawu. Jeśli zestaw jest identyfikowany jako zestaw zaprzyjaźniony, nie trzeba już oznaczać typów i składowych jako publicznych, aby były dostępne dla innych zestawów. Jest to szczególnie wygodne w następujących scenariuszach:

- Podczas testowania jednostkowego, gdy kod testowy jest uruchamiany w osobnym zestawie, ale wymaga dostępu do elementów członkowskich w testowanym zestawie, które `internal` są C# oznaczone `Friend` jako w lub w Visual Basic.

- Podczas tworzenia biblioteki klas, a dodatki do biblioteki są zawarte w oddzielnych zestawach, ale wymagają dostępu do elementów członkowskich w istniejących zestawach, które są `internal` oznaczone C# jako `Friend` w lub w Visual Basic.

## <a name="remarks"></a>Uwagi

Możesz użyć atrybutu, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> aby zidentyfikować jeden lub więcej zaprzyjaźnionych zestawów dla danego zestawu. W poniższym przykładzie zastosowano <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut w *zestawie* a i określa Assembly *AssemblyB* jako zestaw zaprzyjaźniony. Daje to zestawowi *AssemblyB* dostęp do wszystkich typów i członków w *zestawie a* , które są `internal` oznaczone C# jako `Friend` w lub w Visual Basic.

> [!NOTE]
> Podczas kompilowania zestawu, takiego jak *AssemblyB* , który będzie uzyskiwać dostęp do typów wewnętrznych lub wewnętrznych elementów członkowskich innego zestawu, takiego jak *zestaw A*, należy jawnie określić nazwę pliku wyjściowego (*exe* lub *dll*) przy użyciu polecenia **/out** opcja kompilatora. Jest to wymagane, ponieważ kompilator nie wygenerował jeszcze nazwy dla zestawu, który jest tworzony w momencie powiązania z odwołaniami zewnętrznymi. Aby uzyskać więcej informacji, zobacz [/outC#()](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
Imports System
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

Tylko zestawy, które można jawnie określić jako znajomi mogą `internal` uzyskaćC#dostęp ( `Friend` ) lub (Visual Basic) typów i członków. Na przykład, jeśli *AssemblyB* jest znajomością *zestawu* a i *zestawu c* References *AssemblyB*, *zestaw c* nie ma dostępu `internal` do (C#) lub `Friend` (Visual Basic) typów w *zestawie a* .

Kompilator wykonuje pewne podstawowe walidacje nazwy zestawu zaprzyjaźnionego przekazaną do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Jeśli *zestaw A* deklaruje *AssemblyB* jako zestaw zaprzyjaźniony, reguły walidacji są następujące:

- Jeśli *zestaw A* ma silną nazwę, *AssemblyB* musi być również silną nazwą. Nazwa zestawu zaprzyjaźnionego, który jest przesyłany do atrybutu, musi zawierać nazwę zestawu i klucz publiczny klucza o silnej nazwie, który jest używany do podpisywania *AssemblyB*.

     Nazwa zestawu zaprzyjaźnionego, która jest przenoszona <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> do atrybutu, nie może być silną nazwą *AssemblyB*. Nie dołączaj wersji zestawu, kultury, architektury lub tokenu klucza publicznego.

- Jeśli *zestaw A* nie ma silnej nazwy, nazwa zestawu zaprzyjaźnionego powinna zawierać tylko nazwę zestawu. Aby uzyskać więcej informacji, zobacz [jak: Utwórz niepodpisane zaprzyjaźnione zestawy](create-unsigned-friend.md).

- Jeśli *AssemblyB* ma silną nazwę, należy określić klucz silnej nazwy dla *AssemblyB* przy użyciu ustawienia projektu lub opcji kompilatora wiersza `/keyfile` polecenia. Aby uzyskać więcej informacji, zobacz [jak: Utwórz podpisane zaprzyjaźnione](create-signed-friend.md)zestawy.

 <xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa oferuje również możliwość udostępniania typów z następującymi różnicami:

- <xref:System.Security.Permissions.StrongNameIdentityPermission>dotyczy pojedynczego typu, podczas gdy zestaw zaprzyjaźniony ma zastosowanie do całego zestawu.

- Jeśli istnieją setki typów w *zestawie A* , które chcesz udostępnić w *AssemblyB*, musisz dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> je do wszystkich. Jeśli używasz zestawu zaprzyjaźnionego, musisz tylko raz zadeklarować relację zaprzyjaźnioną.

- Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typy, które chcesz udostępnić, muszą być zadeklarowane jako publiczne. Jeśli używasz zestawu zaprzyjaźnionego, typy udostępnione są zadeklarowane jako `internal` (C#) lub `Friend` (Visual Basic).

Aby uzyskać informacje o sposobach uzyskiwania dostępu do `internal` typówC#i metod `Friend` zestawu () lub (Visual Basic) z pliku modułu (pliku z rozszerzeniem *. webmodule* ), zobacz [/moduleassemblynameC#()](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) lub [/ moduleassemblyname — (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Instrukcje: Utwórz niepodpisane zestawy zaprzyjaźnione](create-unsigned-friend.md)
- [Instrukcje: Utwórz podpisane zaprzyjaźnione zestawy](create-signed-friend.md)
- [Zestawy w środowisku .NET](index.md)
- [C#Przewodnik programowania](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
