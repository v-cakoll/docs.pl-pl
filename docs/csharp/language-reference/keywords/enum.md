---
title: enum — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: fb11fb1a81b8407e2585e32d4217e08a75ea19b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605823"
---
# <a name="enum-c-reference"></a>enum (odwołanie w C#)

`enum` Słowo kluczowe jest używane do deklarowania wyliczenia, odrębnego typu, który składa się z zestawu nazwanych stałych o nazwie Lista modułów wyliczających.

Zazwyczaj najlepszym rozwiązaniem jest zdefiniowanie wyliczenia bezpośrednio w przestrzeni nazw, tak aby wszystkie klasy w przestrzeni nazw mogły uzyskać do nich dostęp z taką samą wygodą. Jednak Wyliczenie może być również zagnieżdżone w obrębie klasy lub struktury.

Domyślnie pierwszy moduł wyliczający ma wartość 0, a wartość każdego kolejnego modułu wyliczającego jest zwiększana o 1. Na przykład, w poniższym wyliczeniu `Sat` , `0` `Mon` `Sun` `1` is,isitakdalej`2`.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Moduły wyliczające mogą używać inicjatorów, aby przesłonić wartości domyślne, jak pokazano w poniższym przykładzie.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

W tym wyliczeniu kolejność elementów jest wymuszana od `1` `0`zamiast. Jednakże, w tym stała o wartości 0 jest zalecana. Aby uzyskać więcej informacji, zobacz [typy](../../programming-guide/enumeration-types.md)wyliczeniowe.

Każdy typ wyliczeniowy ma typ podstawowy, który może być dowolnym [typem liczb całkowitych](../builtin-types/integral-numeric-types.md). Typ [char](char.md) nie może być podstawowym typem wyliczenia. Domyślny typ podstawowy elementów wyliczenia to [int](../builtin-types/integral-numeric-types.md). Aby zadeklarować Wyliczenie innego typu całkowitego, takiego jak [Byte](../builtin-types/integral-numeric-types.md), Użyj dwukropka po identyfikatorze, po którym następuje typ, jak pokazano w poniższym przykładzie.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Do zmiennej typu wyliczenia można przypisać dowolną wartość z zakresu typu bazowego; wartości nie są ograniczone do nazwanych stałych.

Wartość `enum E` domyślna jest wartością wygenerowaną przez wyrażenie `(E)0`.

> [!NOTE]
> Moduł wyliczający nie może zawierać białych znaków w nazwie.

Typ podstawowy określa, ile miejsca do magazynowania przydzielono dla każdego modułu wyliczającego. Jednak jawne rzutowanie jest niezbędne do konwersji z `enum` typu na typ całkowity. Na przykład Poniższa `Sun` instrukcja przypisuje moduł wyliczający do zmiennej typu [int](../builtin-types/integral-numeric-types.md) przy użyciu rzutowania do konwersji z `enum` na. `int`

```csharp
int x = (int)Day.Sun;
```

Po zastosowaniu <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia zawierającego elementy, które mogą być połączone z operacją bitową `OR` , atrybut `enum` ma wpływ na zachowanie, gdy jest używany w przypadku niektórych narzędzi. Te zmiany można zauważyć przy użyciu narzędzi, takich jak <xref:System.Console> metody klasy i ewaluatora wyrażeń. (Zobacz trzeci przykład).

## <a name="robust-programming"></a>Niezawodne programowanie

Podobnie jak w przypadku każdej stałej, wszystkie odwołania do poszczególnych wartości wyliczenia są konwertowane na literały numeryczne w czasie kompilacji. Może to powodować problemy z wersjami, jak opisano w [stałych](../../programming-guide/classes-and-structs/constants.md).

Przypisanie dodatkowych wartości do nowych wersji wyliczeń lub zmiana wartości elementów członkowskich wyliczenia w nowej wersji może spowodować problemy z zależnym kodem źródłowym. Wartości wyliczeniowe często są używane w instrukcjach [Switch](switch.md) . Jeśli do `enum` typu Dodano dodatkowe elementy, sekcja domyślna instrukcji switch może zostać nieoczekiwanie wybrana.

Jeśli inni deweloperzy używają kodu, należy podać wskazówki dotyczące sposobu reakcji ich kodu, jeśli nowe elementy są dodawane do dowolnego `enum` typu.

## <a name="example"></a>Przykład

W poniższym przykładzie jest zadeklarowane Wyliczenie `Day`. Dwa moduły wyliczające są jawnie konwertowane na liczbę całkowitą i są przypisane do zmiennych całkowitych.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Przykład

W poniższym przykładzie opcja typu podstawowego służy do deklarowania, `enum` którego składowe są typu. `long` Należy zauważyć, że mimo że typ podstawowy wyliczenia to `long`, elementy członkowskie wyliczenia nadal muszą być jawnie konwertowane na typ `long` za pomocą rzutowania.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje użycie i efekt <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu `enum` w deklaracji.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Komentarze

W przypadku usunięcia `Flags`tego przykładu zostaną wyświetlone następujące wartości:

`5`

`5`

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Typy wyliczeniowe](../../programming-guide/enumeration-types.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)
- [Wyliczeniowe konwencje nazewnictwa](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
