---
title: Fixed Statement - C# odwołania
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 4ef334f6d200e75f29e22a9586f4538309797942
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661675"
---
# <a name="fixed-statement-c-reference"></a>fixed — Instrukcja (odwołanie w C#)

`fixed` Instrukcji zapobiega przemieszczanie zmienną ruchome moduł odśmiecania pamięci. `fixed` Instrukcji jest dozwolona tylko w [niebezpieczne](unsafe.md) kontekstu. `fixed` można również utworzyć [stałych buforów o rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Instrukcja ustawia wskaźnik zarządzanego zmiennej i "przypięć" tej zmiennej podczas wykonywania instrukcji. Wskaźniki do zmiennych, ruchome zarządzane są przydatne tylko w `fixed` kontekstu. Bez `fixed` kontekstu, wyrzucanie elementów bezużytecznych może przenosić zmienne nieprzewidywalny. Kompilator języka C# tylko umożliwia przypisywanie wskaźnik do zmiennej zarządzanych w `fixed` instrukcji.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Aby zainicjować wskaźnik, należy za pomocą tablicy, ciąg, bufora o stałym rozmiarze lub adres zmiennej. Poniższy przykład ilustruje użycie zmiennej adresów, tablic i ciągów. Aby uzyskać więcej informacji o stałym rozmiarze buforów, zobacz [ustalony rozmiar buforów](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Począwszy od C# 7.3, `fixed` instrukcji operuje na dodatkowe typy poza tablice, ciągi, bufory o stałym rozmiarze lub niezarządzanego zmiennych. Dowolny typ, który implementuje metodę o nazwie `GetPinnableReference` można przypiąć. `GetPinnableReference` Musi zwracać `ref` zmienną typu niezarządzanego. Zobacz temat w [typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md) Aby uzyskać więcej informacji. Typy .NET <xref:System.Span%601?displayProperty=nameWithType> i <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> wprowadzone w programie .NET Core 2.0 upewnij Użyj tego wzorca i mogą być przypinane. Jest to pokazane w poniższym przykładzie:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Jeśli tworzysz typy, które należy wziąć udział w tym wzorcu, zobacz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> przykład implementacja wzorca.

Mogą być inicjowane wielu wskaźników w jednej instrukcji, jeśli są tego samego typu:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Aby zainicjować wskaźników różnego typu, po prostu zagnieździć `fixed` instrukcje, jak pokazano w poniższym przykładzie.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Po wykonaniu kodu w instrukcji wszystkie przypięte zmienne są nieprzypięte i wyrzucania elementów bezużytecznych. W związku z tym, nie mogą wskazywać tych zmiennych na zewnątrz `fixed` instrukcji. Zmienne zadeklarowane w `fixed` instrukcji są ograniczone do tej instrukcji, ułatwiając to:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Wskaźniki są inicjowane w `fixed` instrukcje są zmienne tylko do odczytu. Jeśli chcesz zmodyfikować wartość wskaźnika, należy zadeklarować zmienną drugi wskaźnik i zmodyfikować to. Zmienna zadeklarowana w `fixed` instrukcji nie można zmodyfikować:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

W trybie bezpiecznym można przydzielić pamięci na stosie, w którym nie podlega wyrzucania elementów bezużytecznych i dlatego nie trzeba przypiąć. Aby uzyskać więcej informacji, zobacz [stackalloc](stackalloc.md).

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a>Specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [unsafe](unsafe.md)
- [Bufory o ustalonym rozmiarze](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
