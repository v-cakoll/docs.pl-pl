---
title: Przyjazne zestawy
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348176"
---
# <a name="friend-assemblies"></a>Przyjazne zestawy

*Zestaw znajomego* jest zestaw, który może uzyskać dostęp do [wewnętrznego](../../csharp/language-reference/keywords/internal.md) innego zestawu (C#) lub [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) typów i elementów członkowskich. Jeśli zidentyfikujesz zestaw jako zestaw znajomego, nie trzeba już oznaczać typy i elementy członkowskie jako publiczne, aby były dostępne dla nich przez inne zestawy. Jest to szczególnie wygodne w następujących scenariuszach:

- Podczas testowania jednostkowego, gdy kod testu jest uruchamiany w oddzielnym zestawie, `internal` ale wymaga `Friend` dostępu do elementów członkowskich w testowanym zestawie, które są oznaczone jako c# lub w języku Visual Basic.

- Podczas opracowywania biblioteki klas i dodatki do biblioteki są zawarte w oddzielnych zestawów, ale wymagają `internal` dostępu do `Friend` elementów członkowskich w istniejących zestawów, które są oznaczone jako w języku C# lub w języku Visual Basic.

## <a name="remarks"></a>Uwagi

Atrybut użyje <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> do zidentyfikowania jednego lub więcej zestawów znajomych dla danego zestawu. W poniższym <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> przykładzie użyto atrybutu w *zestawie A* i określa zestaw *AssemblyB* jako zestaw znajomego. Daje to *assemblyAssemblyB* dostęp do wszystkich typów i `internal` elementów członkowskich `Friend` w *zestawie A,* które są oznaczone jako c# lub w języku Visual Basic.

> [!NOTE]
> Podczas kompilowania zestawu, takiego jak *AssemblyB,* który będzie uzyskiwał dostęp do wewnętrznych typów lub wewnętrznych elementów członkowskich innego zestawu, takiego jak *zestaw A,* należy jawnie określić nazwę pliku wyjściowego *(exe* lub *dll)* za pomocą opcji **kompilatora -out.** Jest to wymagane, ponieważ kompilator nie wygenerował jeszcze nazwę zestawu, który tworzy w czasie jest powiązany z odwołaniami zewnętrznymi. Aby uzyskać więcej informacji, zobacz [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) lub [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

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

Tylko zestawy, które jawnie określić `internal` jako znajomi `Friend` mogą uzyskać dostęp (C#) lub (Visual Basic) typy i elementy członkowskie. Na przykład jeśli *AssemblyB* jest przyjacielem *zestawu A* i *zestawu C* odwołuje się do *AssemblyB,* *zestaw C* nie ma dostępu `internal` do (C#) lub `Friend` (Visual Basic) typów w zestawie *A*.

Kompilator wykonuje podstawowe sprawdzanie poprawności nazwy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zestawu znajomego przekazany do atrybutu. Jeśli *zestaw A* deklaruje *AssemblyB* jako zestaw przyjaciela, reguły sprawdzania poprawności są następujące:

- Jeśli *zestaw A* jest silny *nazwie, AssemblyB* musi być również silne ja. Nazwa zestawu znajomego, która jest przekazywana do atrybutu musi składać się z nazwy zestawu i klucza publicznego klucza silnej nazwy, który jest używany do podpisania *AssemblyB*.

     Nazwa zestawu znajomego, która <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> jest przekazywana do atrybutu, nie może być silną nazwą *AssemblyB*. Nie należy dołączać wersji zestawu, kultury, architektury ani tokenu klucza publicznego.

- Jeśli *zestaw A* nie jest silny nazwie, nazwa zestawu znajomego powinna składać się tylko z nazwy zestawu. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie niepodpisanych zestawów znajomych](create-unsigned-friend.md).

- Jeśli *AssemblyB* jest silny o nazwie, należy określić klucz silnej nazwy *dla AssemblyB* przy użyciu ustawienia projektu lub opcji kompilatora wiersza `/keyfile` polecenia. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie podpisanych zestawów znajomych](create-signed-friend.md).

 Klasa <xref:System.Security.Permissions.StrongNameIdentityPermission> zapewnia również możliwość udostępniania typów, z następującymi różnicami:

- <xref:System.Security.Permissions.StrongNameIdentityPermission>dotyczy pojedynczego typu, podczas gdy zespół znajomego ma zastosowanie do całego złożenia.

- Jeśli w *zestawie A* istnieją setki typów, które chcesz udostępnić <xref:System.Security.Permissions.StrongNameIdentityPermission> *zestawowi B,* należy dodać je wszystkie. Jeśli używasz zestawu znajomych, wystarczy zadeklarować relację przyjaciela tylko raz.

- Jeśli używasz, <xref:System.Security.Permissions.StrongNameIdentityPermission>typy, które chcesz udostępnić muszą być zadeklarowane jako publiczne. Jeśli używasz zestawu znajomego, typy udostępnione `internal` są deklarowane `Friend` jako (C#) lub (Visual Basic).

Aby uzyskać informacje dotyczące uzyskiwania `internal` dostępu do `Friend` typów i metod zestawu (C#) lub (Visual Basic) z pliku modułu (pliku z rozszerzeniem *.netmodule),* zobacz [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) lub [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Jak: Tworzenie niepodpisanych zestawów znajomych](create-unsigned-friend.md)
- [Jak: Tworzenie podpisanych zestawów znajomych](create-signed-friend.md)
- [Zestawy w środowisku .NET](index.md)
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
- [Koncepcje programowania (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
