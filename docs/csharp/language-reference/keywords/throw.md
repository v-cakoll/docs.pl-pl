---
title: throw - Odwołanie do języka C#
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 04d3138e3390627355b4b2d4e25c6b00248cec1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399337"
---
# <a name="throw-c-reference"></a>throw (odwołanie w C#)

Sygnalizuje wystąpienie wyjątku podczas wykonywania programu.  
  
## <a name="remarks"></a>Uwagi

Składnia `throw` jest:

```csharp
throw [e];
```

gdzie `e` jest wystąpienieklasy pochodzącej <xref:System.Exception?displayProperty=nameWithType>z . W poniższym `throw` przykładzie użyto <xref:System.IndexOutOfRangeException> instrukcji do wyrzucania, jeśli argument przekazany do metody o nazwie `GetNumber` nie odpowiada prawidłowy indeks tablicy wewnętrznej.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Wywoływanie metody następnie `try-catch` `try-catch-finally` użyć lub bloku do obsługi wyjątek. Poniższy przykład obsługuje wyjątek zgłoszony `GetNumber` przez metodę.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Ponowne zgłaszanie wyjątku

`throw`może być również `catch` używany w bloku, aby ponownie `catch` zgłosić wyjątek obsługiwany w bloku.  W tym `throw` przypadku nie ma argumentu wyjątku. Jest to najbardziej przydatne, gdy metoda przekazuje argument z obiektu wywołującego do innej metody biblioteki, a metoda biblioteki zgłasza wyjątek, który musi zostać przekazany do obiektu wywołującego. Na przykład w poniższym przykładzie <xref:System.NullReferenceException> ponownie zgłasza, który jest generowany podczas próby pobrania pierwszego znaku niezainicjowanego ciągu.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Można również użyć `throw e` składni `catch` w bloku, aby utworzyć wystąpienie nowego wyjątku, który można przekazać do obiektu wywołującego. W takim przypadku ślad stosu oryginalnego wyjątku, który jest dostępny z <xref:System.Exception.StackTrace> właściwości, nie jest zachowywany.

## <a name="the-throw-expression"></a>Wyrażenie `throw`

Począwszy od języka C# 7.0, `throw` może służyć jako wyrażenie, a także instrukcji. Dzięki temu wyjątek wyjątek w kontekstach, które wcześniej nie były obsługiwane. Należą do nich:

- [operatora warunkowego](../operators/conditional-operator.md). W poniższym `throw` przykładzie użyto <xref:System.ArgumentException> wyrażenia do wyrzucania, jeśli metoda jest przekazywana tablicy pustyciąg. Przed C# 7.0, ta logika `if` / `else` musi pojawić się w instrukcji.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [operatora zerowego łączenia](../operators/null-coalescing-operator.md). W poniższym `throw` przykładzie wyrażenie jest używane z operatorem łączenia wartości null, aby zgłosić wyjątek, jeśli ciąg przypisany do `Name` właściwości jest `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) lub metoda osażeniu. W poniższym przykładzie przedstawiono metodę zabudowaną <xref:System.InvalidCastException> wyrażeniem, która <xref:System.DateTime> zgłasza, ponieważ konwersja na wartość nie jest obsługiwana.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
