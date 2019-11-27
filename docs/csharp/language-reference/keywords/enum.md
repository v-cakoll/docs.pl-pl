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
ms.openlocfilehash: 639a3a01c9c4da13e0212bd0230acbd2af170b25
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428523"
---
# <a name="enum-c-reference"></a>enum (odwołanie w C#)

Słowo kluczowe `enum` jest używane do deklarowania wyliczenia, odrębnego typu, który składa się z zestawu nazwanych stałych nazywanych listą Enumerator.

Zazwyczaj najlepszym rozwiązaniem jest zdefiniowanie wyliczenia bezpośrednio w przestrzeni nazw, tak aby wszystkie klasy w przestrzeni nazw mogły uzyskać do nich dostęp z taką samą wygodą. Jednak Wyliczenie może być również zagnieżdżone w obrębie klasy lub struktury.

Domyślnie pierwszy moduł wyliczający ma wartość 0, a wartość każdego kolejnego modułu wyliczającego jest zwiększana o 1. Na przykład w poniższym wyliczeniu `Sat` jest `0`, `Sun` jest `1`, `Mon` jest `2`i tak dalej.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Moduły wyliczające mogą używać inicjatorów, aby przesłonić wartości domyślne, jak pokazano w poniższym przykładzie.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

W tym wyliczeniu kolejność elementów musi rozpoczynać się od `1`, a nie `0`. Jednakże, w tym stała o wartości 0 jest zalecana. Aby uzyskać więcej informacji, zobacz [typy wyliczeniowe](../../programming-guide/enumeration-types.md).

Każdy typ wyliczeniowy ma typ podstawowy, który może być dowolnym [typem liczb całkowitych](../builtin-types/integral-numeric-types.md). Typ [char](../builtin-types/char.md) nie może być podstawowym typem wyliczenia. Domyślny typ podstawowy elementów wyliczenia to [int](../builtin-types/integral-numeric-types.md). Aby zadeklarować Wyliczenie innego typu całkowitego, takiego jak [Byte](../builtin-types/integral-numeric-types.md), Użyj dwukropka po identyfikatorze, po którym następuje typ, jak pokazano w poniższym przykładzie.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Do zmiennej typu wyliczenia można przypisać dowolną wartość z zakresu typu bazowego; wartości nie są ograniczone do nazwanych stałych.

Wartość domyślna `enum E` jest wartością wygenerowaną przez wyrażenie `(E)0`.

> [!NOTE]
> Moduł wyliczający nie może zawierać białych znaków w nazwie.

Typ podstawowy określa, ile miejsca do magazynowania przydzielono dla każdego modułu wyliczającego. Jednak jawne rzutowanie jest niezbędne do konwersji z typu `enum` na typ całkowity. Na przykład poniższa instrukcja przypisuje moduł wyliczający `Sun` do zmiennej typu [int](../builtin-types/integral-numeric-types.md) przy użyciu rzutowania do konwersji z `enum` do `int`.

```csharp
int x = (int)Day.Sun;
```

Po zastosowaniu <xref:System.FlagsAttribute?displayProperty=nameWithType> do wyliczenia zawierającego elementy, które mogą być połączone z operacją bitową `OR`, atrybut ma wpływ na zachowanie `enum`, gdy jest używany z niektórymi narzędziami. Te zmiany można zauważyć przy użyciu narzędzi, takich jak metody klasy <xref:System.Console> i ewaluatora wyrażeń. (Zobacz trzeci przykład).

## <a name="robust-programming"></a>Niezawodne programowanie

Podobnie jak w przypadku każdej stałej, wszystkie odwołania do poszczególnych wartości wyliczenia są konwertowane na literały numeryczne w czasie kompilacji. Może to powodować problemy z wersjami, jak opisano w [stałych](../../programming-guide/classes-and-structs/constants.md).

Przypisanie dodatkowych wartości do nowych wersji wyliczeń lub zmiana wartości elementów członkowskich wyliczenia w nowej wersji może spowodować problemy z zależnym kodem źródłowym. Wartości wyliczeniowe często są używane w instrukcjach [Switch](switch.md) . Jeśli dodano dodatkowe elementy do typu `enum`, sekcja domyślna instrukcji switch może zostać nieoczekiwanie wybrana.

Jeśli inni deweloperzy używają kodu, należy podać wskazówki dotyczące sposobu reakcji ich kodu, jeśli nowe elementy są dodawane do dowolnego typu `enum`.

## <a name="example"></a>Przykład

W poniższym przykładzie jest zadeklarowane Wyliczenie `Day`. Dwa moduły wyliczające są jawnie konwertowane na liczbę całkowitą i są przypisane do zmiennych całkowitych.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Przykład

W poniższym przykładzie opcja typu podstawowego służy do deklarowania `enum`, których składowe są typu `long`. Należy zauważyć, że mimo że typ podstawowy wyliczenia jest `long`, elementy członkowskie wyliczenia nadal muszą być jawnie konwertowane na typ `long` za pomocą rzutowania.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje użycie i efekt atrybutu <xref:System.FlagsAttribute?displayProperty=nameWithType> w deklaracji `enum`.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Komentarze

W przypadku usunięcia `Flags`przykład zostanie wyświetlona następująca wartość:

`5`

`5`

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Typy wyliczeniowe](../../programming-guide/enumeration-types.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Wyliczeniowe konwencje nazewnictwa](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
