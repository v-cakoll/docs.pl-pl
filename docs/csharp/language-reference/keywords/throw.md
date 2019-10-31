---
title: throw — C# odwołanie
ms.custom: seodec18
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: f274802c84ff8f3dd2588db8b83a0d0de36d2d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101773"
---
# <a name="throw-c-reference"></a>throw (odwołanie w C#)

Sygnalizuje wystąpienie wyjątku podczas wykonywania programu.  
  
## <a name="remarks"></a>Uwagi

Składnia `throw` jest następująca:

```csharp
throw [e];
```

gdzie `e` jest wystąpieniem klasy pochodzącej od <xref:System.Exception?displayProperty=nameWithType>. Poniższy przykład używa instrukcji `throw`, aby zgłosić <xref:System.IndexOutOfRangeException>, jeśli argument przesłany do metody o nazwie `GetNumber` nie odpowiada prawidłowemu indeksowi tablicy wewnętrznej.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

Metody wywołujące stosują następnie `try-catch` lub `try-catch-finally` bloku, aby obsłużyć zgłoszony wyjątek. Poniższy przykład obsługuje wyjątek zgłoszony przez metodę `GetNumber`.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a>Ponowne zgłaszanie wyjątku

`throw` można również użyć w bloku `catch`, aby ponownie zgłosić wyjątek obsłużony w bloku `catch`.  W tym przypadku `throw` nie przyjmuje operandu wyjątku. Jest to najbardziej przydatne, gdy metoda przekazuje argument od wywołującego do innej metody biblioteki, a metoda Library zgłasza wyjątek, który musi zostać przekazana do obiektu wywołującego. Na przykład poniższy przykład ponownie generuje <xref:System.NullReferenceException>, który jest zgłaszany podczas próby pobrania pierwszego znaku niezainicjowanego ciągu.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> Możesz również użyć składni `throw e` w bloku `catch`, aby utworzyć wystąpienie nowego wyjątku przekazanego do obiektu wywołującego. W takim przypadku śledzenie stosu oryginalnego wyjątku, który jest dostępny we właściwości <xref:System.Exception.StackTrace>, nie jest zachowywane.

## <a name="the-throw-expression"></a>Wyrażenie `throw`

Począwszy od C# 7,0, `throw` może służyć jako wyrażenie, a także instrukcja. Pozwala to na wyrzucanie wyjątku w kontekstach, które były wcześniej nieobsługiwane. Należą do nich następujące elementy:

- [operator warunkowy](../operators/conditional-operator.md). Poniższy przykład używa wyrażenia `throw`, aby zgłosić <xref:System.ArgumentException>, jeśli metoda jest przenoszona pustą tablicę ciągów. Przed C# 7,0, ta logika powinna być wyświetlana w instrukcji `if`/`else`.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- [operator łączenia wartości null](../operators/null-coalescing-operator.md). W poniższym przykładzie wyrażenie `throw` jest używane z operatorem łączenia wartości null, aby zgłosić wyjątek, jeśli ciąg przypisany do właściwości `Name` jest `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- wyrażenie wyrażenia [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) lub metody. Poniższy przykład ilustruje metodę zanikającą z wyrażenia, która zgłasza <xref:System.InvalidCastException>, ponieważ konwersja do wartości <xref:System.DateTime> nie jest obsługiwana.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
