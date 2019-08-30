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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a9a235da06427e12bb5866a48f76f9c5896a572
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168747"
---
# <a name="throw-c-reference"></a>throw (odwołanie w C#)

Sygnalizuje wystąpienie wyjątku podczas wykonywania programu.  
  
## <a name="remarks"></a>Uwagi

Składnia `throw` :

```csharp
throw [e]
```

gdzie `e` to wystąpienie klasy <xref:System.Exception?displayProperty=nameWithType>pochodnej. Poniższy przykład używa instrukcji, `throw` aby <xref:System.IndexOutOfRangeException> zgłosić, czy argument przesłany do metody o nazwie `GetNumber` nie odpowiada prawidłowemu indeksowi tablicy wewnętrznej.

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Metody wywołujące używają `try-catch` następnie bloku lub `try-catch-finally` do obsługi zgłoszonego wyjątku. Poniższy przykład obsługuje wyjątek zgłoszony przez `GetNumber` metodę.

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Ponowne zgłaszanie wyjątku

`throw`można go również użyć w `catch` bloku, aby ponownie zgłosić wyjątek obsłużony `catch` w bloku.  W tym przypadku `throw` nie przyjmuje operandu wyjątku. Jest to najbardziej przydatne, gdy metoda przekazuje argument od wywołującego do innej metody biblioteki, a metoda Library zgłasza wyjątek, który musi zostać przekazana do obiektu wywołującego. Na przykład poniższy przykład generuje ponownie zdarzenie <xref:System.NullReferenceException> , które jest zgłaszane podczas próby pobrania pierwszego znaku niezainicjowanego ciągu.

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Możesz również użyć `throw e` składni `catch` w bloku, aby utworzyć wystąpienie nowego wyjątku przekazywanego do obiektu wywołującego. W takim przypadku śledzenie stosu oryginalnego wyjątku, który jest dostępny we <xref:System.Exception.StackTrace> właściwości, nie jest zachowywane.

## <a name="the-throw-expression"></a>`throw` Wyrażenie

Począwszy od C# 7,0, `throw` można użyć jako wyrażenia, a także instrukcji. Pozwala to na wyrzucanie wyjątku w kontekstach, które były wcześniej nieobsługiwane. Należą do nich następujące elementy:

- [operator warunkowy](../operators/conditional-operator.md). Poniższy przykład używa `throw` wyrażenia, aby <xref:System.ArgumentException> zgłosić, czy metoda jest przenoszona pustą tablicę ciągów. Przed C# 7,0, ta logika musi pojawić się w `if` / `else` instrukcji.

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [operator łączenia wartości null](../operators/null-coalescing-operator.md). W poniższym przykładzie `throw` wyrażenie jest używane z operatorem łączenia wartości null, aby zgłosić wyjątek, jeśli ciąg przypisany `Name` do właściwości jest `null`.

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  

- wyrażenie wyrażenia [lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) lub metody. Poniższy przykład ilustruje metodę zanikającą z wyrażenia, która zgłasza <xref:System.InvalidCastException> , ponieważ konwersja <xref:System.DateTime> do wartości nie jest obsługiwana.

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  

## <a name="c-language-specification"></a>specyfikacja języka C#  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [try-catch](try-catch.md)
- [Słowa kluczowe języka C#](index.md)
- [Instrukcje: Jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
