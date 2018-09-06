---
title: Enum — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: a64559ac1127f5ec296cf3892dd521c3ad8ac2be
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875473"
---
# <a name="enum-c-reference"></a>enum (odwołanie w C#)

`enum` Słowo kluczowe jest używane do deklarowania wyliczania, typem samodzielnym, który zawiera zestaw nazwanych stałych zwanego listą modułów wyliczających.  

Zazwyczaj najlepiej jest zdefiniowanie wyliczenia bezpośrednio w przestrzeni nazw, tak, aby wszystkie klasy w przestrzeni nazw do niego dostęp za pomocą równy wygody. Jednak wyliczenia może być zagnieżdżona w klasie lub strukturze.

Domyślnie pierwszy moduł wyliczający ma wartość 0, a wartość każdego kolejnych moduł wyliczający jest zwiększana o 1. Na przykład w następujących wyliczenia `Sat` jest `0`, `Sun` jest `1`, `Mon` jest `2`, i tak dalej.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Moduły wyliczające umożliwia inicjatory przesłonić wartości domyślne, jak pokazano w poniższym przykładzie.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

W tym wyliczeniu sekwencję elementów jest zmuszony do uruchamiania z `1` zamiast `0`. Jednak zaleca się tym stałą, który ma wartość 0. Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe](../../programming-guide/enumeration-types.md).

Każdy typ wyliczenia ma podstawowy typ, który może być dowolnego typu całkowitoliczbowego z wyjątkiem [char](char.md). Domyślny typ podstawowy wyliczenia elementów to [int](int.md). Aby zadeklarować wyliczenie innego typu całkowitego, takich jak [bajtów](byte.md), użyj dwukropka po identyfikatorze, a następnie według typu, jak pokazano w poniższym przykładzie.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Zatwierdzone typy wyliczenia [bajtów](byte.md), [sbyte](sbyte.md), [krótki](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [długie](long.md), lub [ulong](ulong.md).

Zmienna typu `Day` można przypisać dowolną wartość z zakresu typu podstawowego; wartości nie są ograniczone do nazwanych stałych.

Wartość domyślna `enum E` jest wartością produkowane przez wyrażenie `(E)0`.

> [!NOTE]
> Moduł wyliczający nie może zawierać biały znak w nazwie.

Podstawowy typ Określa, ile pamięci masowej jest przydzielany dla każdego typu wyliczeniowego. Jednak jawnego rzutowania jest niezbędne do konwersji z `enum` typu na typ całkowitoliczbowy. Na przykład następująca instrukcja przypisuje modułu wyliczającego `Sun` do zmiennej typu [int](int.md) przy użyciu rzutowanie do konwersji z `enum` do `int`.

```csharp
int x = (int)Day.Sun;
```

Po zastosowaniu <xref:System.FlagsAttribute?displayProperty=nameWithType> z wyliczeniem, który zawiera elementy, które mogą być łączone z bitową `OR` operacji, ten atrybut ma wpływ na zachowanie `enum` gdy jest używany z narzędziami. Można zauważyć te zmiany, korzystając z narzędzi takich jak <xref:System.Console> klas, metod i ewaluatora wyrażenia. (Zobacz trzeci przykład).

## <a name="robust-programming"></a>Skuteczne programowanie

Podobnie jak w przypadku dowolną stałą wszystkie odwołania do poszczególnych wartości wyliczenia są konwertowane na literały numeryczne w czasie kompilacji. To utworzenie potencjalne problemy z wersjonowaniem, zgodnie z opisem w [stałe](../../programming-guide/classes-and-structs/constants.md).

Przypisywanie dodatkowych wartości do nowych wersji wyliczenia lub zmiana wartości elementów członkowskich wyliczenia w nowej wersji, może powodować problemy, które kodu źródłowego zależnych. Wartości wyliczeniowe są często używane w [Przełącz](switch.md) instrukcji. Jeśli dodatkowe elementy zostały dodane do `enum` nieoczekiwanie można wybrać domyślną sekcję instrukcji switch typu.

Użycie kodu, inni deweloperzy dostarczają wytyczne dotyczące sposobu ich kod powinien reagować, jeśli nowe elementy są dodawane do dowolnej `enum` typów.

## <a name="example"></a>Przykład

W poniższym przykładzie wyliczenie `Day`, jest zadeklarowana. Dwa moduły wyliczające są jawnie konwertowany na liczbę całkowitą i przypisane do zmiennych całkowitych.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Przykład

W poniższym przykładzie opcja Typ podstawowy jest używane do deklarowania `enum` której członkami są typu `long`. Należy zauważyć, że nawet jeśli jest podstawowym typem wyliczenia `long`, elementy członkowskie wyliczenia nadal muszą być jawnie konwertowane na typ `long` przy użyciu rzutowania.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Przykład

Poniższy przykład kodu ilustruje stosowanie i efekt <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutu na `enum` deklaracji.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Komentarze

Jeśli usuniesz `Flags`, w przykładzie są wyświetlane następujące wartości:

`5`

`5`

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)  
- [Typy wyliczeniowe](../../programming-guide/enumeration-types.md)  
- [Słowa kluczowe języka C#](index.md)  
- [Tabela typów całkowitych](integral-types-table.md)  
- [Tabela typów wbudowanych](built-in-types-table.md)  
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)  
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)  
- [Konwencje nazewnictwa typu wyliczeniowego](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
