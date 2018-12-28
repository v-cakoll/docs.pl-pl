---
title: Użycie dyrektywy - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 8ed1386d0da802e00dc6cf4b8d56b27fbb6226d4
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612598"
---
# <a name="using-directive-c-reference"></a>Using — Dyrektywa (C# odwołania)

`using` Dyrektywy ma trzy zastosowań:

- Aby zezwolić na używanie typów w przestrzeni nazw, tak, aby nie trzeba Zakwalifikuj użycie typu w tej przestrzeni nazw:

    ```csharp
    using System.Text;
    ```

- Aby umożliwić dostęp do statycznych elementów członkowskich i typy zagnieżdżone typu bez konieczności kwalifikuj dostęp do nazwą typu.

    ```csharp
    using static System.Math;
    ```

    Aby uzyskać więcej informacji, zobacz [using static, dyrektywa](using-static.md).

- Aby utworzyć alias dla przestrzeni nazw lub typu. Jest to nazywane *użycie dyrektywy alias*.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

`using` Słowo kluczowe jest również używane do tworzenia *za pomocą instrukcji*, co pomóc, upewnij się, że <xref:System.IDisposable> obiektów, takich jak pliki i czcionki są obsługiwane poprawnie. Zobacz [za pomocą instrukcji](using-statement.md) Aby uzyskać więcej informacji.

## <a name="using-static-type"></a>Za pomocą typu statycznego

Statyczne elementy członkowskie typu dostęp bez konieczności kwalifikuj dostęp do nazwą typu:

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

Zakres `using` dyrektywa jest ograniczona do pliku, w której występuje.

`using` Dyrektywy może się pojawić:

- Na początku pliku kodu źródłowego, przed żadnych definicji przestrzeni nazw lub typu.
- W dowolnym obszarze nazw, ale przed każdą przestrzeń nazw lub typów zadeklarowane w tej przestrzeni nazw.

W przeciwnym razie, błąd kompilatora [CS1529](../../misc/cs1529.md) jest generowany.

Utwórz `using` alias — dyrektywa, aby ułatwić kwalifikują się do przestrzeni nazw lub typ identyfikatora. W dowolnym `using` dyrektywy, w pełni kwalifikowaną przestrzeń nazw lub typ należy użyć niezależnie od wartości `using` dyrektyw, które pochodzą przed nią. Nie `using` alias mogą być używane w deklaracji `using` dyrektywy. Na przykład poniższa generuje błąd kompilatora:

```csharp
using s = System.Text;
using s.RegularExpressions;
```

Utwórz `using` dyrektywy na używanie typów w przestrzeni nazw bez konieczności określania przestrzeni nazw. A `using` dyrektywy nie umożliwiają dostęp do wszelkich przestrzenie nazw, które są zagnieżdżone w przestrzeni nazw, należy określić.

Przestrzenie nazw są dostępne w dwóch kategorii: zdefiniowane przez użytkownika i zdefiniowane przez system. Zdefiniowane przez użytkownika przestrzenie nazw są przestrzenie nazw zdefiniowane w kodzie. Aby uzyskać listę nazw zdefiniowaną przez system, zobacz [przeglądarka interfejsu API .NET](https://docs.microsoft.com/dotnet/api/).

Przykłady dotyczące odwoływania się do metody w innych zestawach, zobacz [tworzenie i użyj zestawów przy użyciu wiersza polecenia](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).

## <a name="example-1"></a>Przykład 1

Poniższy przykład pokazuje, jak zdefiniować i zastosować `using` alias dla przestrzeni nazw:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Using — dyrektywa alias nie może mieć to otwarty typ ogólny po prawej stronie. Na przykład nie można utworzyć za pomocą aliasu dla `List<T>`, ale można utworzyć dla `List<int>`.

## <a name="example-2"></a>Przykład 2

Poniższy przykład pokazuje jak zdefiniować `using` dyrektywy i `using` alias dla klasy:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [dyrektywy Using](~/_csharplang/spec/namespaces.md#using-directives) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Używanie przestrzeni nazw](../../programming-guide/namespaces/using-namespaces.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe przestrzeni nazw](namespace-keywords.md)
- [Przestrzenie nazw](../../programming-guide/namespaces/index.md)
- [using, instrukcja](using-statement.md)
