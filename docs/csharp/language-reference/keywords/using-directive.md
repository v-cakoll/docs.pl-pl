---
title: za pomocą dyrektywy - C# Odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 4f7ddad8c3dc12391ef6bf345a73ebb384400b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093152"
---
# <a name="using-directive-c-reference"></a>za pomocą dyrektywy (C# Reference)

Dyrektywa `using` ma trzy zastosowania:

- Aby zezwolić na używanie typów w obszarze nazw, dzięki czemu nie trzeba kwalifikować użycie typu w tym obszarze nazw:

    ```csharp
    using System.Text;
    ```

- Aby umożliwić dostęp do elementów statycznych i zagnieżdżonych typów typu bez konieczności kwalifikowania dostępu z nazwą typu.

    ```csharp
    using static System.Math;
    ```

    Aby uzyskać więcej informacji, zobacz [using static dyrektywy](using-static.md).

- Aby utworzyć alias dla obszaru nazw lub typu. Jest to tak zwana *dyrektywa używająca aliasu*.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

Słowo `using` kluczowe jest również używane do tworzenia <xref:System.IDisposable> za pomocą *instrukcji*, które pomagają zapewnić, że obiekty, takie jak pliki i czcionki są obsługiwane poprawnie. Aby uzyskać więcej [informacji, zobacz korzystanie z instrukcji.](using-statement.md)

## <a name="using-static-type"></a>Korzystanie z typu statycznego

Dostęp do statycznych elementów członkowskich typu można uzyskać bez konieczności kwalifikowania dostępu przy użyciu nazwy typu:

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a>Uwagi

Zakres `using` dyrektywy jest ograniczony do pliku, w którym się pojawia.

Dyrektywa `using` może pojawić się:

- Na początku pliku kodu źródłowego, przed dowolnym obszarem nazw lub definicjami typów.
- W dowolnym obszarze nazw, ale przed dowolnym obszarem nazw lub typami zadeklarowanym w tym obszarze nazw.

W przeciwnym razie generowany jest błąd kompilatora [CS1529.](../../misc/cs1529.md)

Utwórz `using` dyrektywę aliasu, aby ułatwić kwalifikowanie identyfikatora do obszaru nazw lub typu. W `using` każdej dyrektywie w pełni kwalifikowana przestrzeń nazw lub `using` typ muszą być używane niezależnie od dyrektyw, które są przed nim. Nie `using` alias może być używany `using` w deklaracji dyrektywy. Na przykład następujące generuje błąd kompilatora:

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

Utwórz `using` dyrektywę, aby używać typów w obszarze nazw bez konieczności określania obszaru nazw. Dyrektywa `using` nie daje dostępu do żadnych obszarów nazw, które są zagnieżdżone w określonym obszarze nazw.

Przestrzenie nazw są dostępne w dwóch kategoriach: zdefiniowane przez użytkownika i zdefiniowane przez system. Przestrzenie nazw zdefiniowane przez użytkownika to obszary nazw zdefiniowane w kodzie. Aby uzyskać listę obszarów nazw zdefiniowanych przez system, zobacz [Przeglądarka interfejsu API .NET](../../../../api/index.md).

## <a name="example-1"></a>Przykład 1

W poniższym przykładzie pokazano, `using` jak zdefiniować alias i używać go dla obszaru nazw:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

A using alias dyrektywy nie może mieć otwarty typ ogólny po prawej stronie. Na przykład nie można utworzyć aliasu używającego `List<T>`dla , `List<int>`ale można go utworzyć dla .

## <a name="example-2"></a>Przykład 2

W poniższym przykładzie pokazano, jak zdefiniować dyrektywę `using` i `using` alias dla klasy:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Korzystanie z dyrektyw](~/_csharplang/spec/namespaces.md#using-directives) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
- [Słowa kluczowe języka C#](index.md)
- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
- [za pomocą instrukcji](using-statement.md)
