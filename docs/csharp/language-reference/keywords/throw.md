---
title: "throw (odwołanie w C#)"
ms.date: 03/02/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56bd8f8b6bfcc7c8f1eb2df6ac157e28adac331
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="throw-c-reference"></a>throw (odwołanie w C#)
Sygnalizuje wystąpienie Wystąpił wyjątek podczas wykonywania programu.  
  
## <a name="remarks"></a>Uwagi

Składnia `throw` jest:

```csharp
throw [e]
```
gdzie `e` jest wystąpieniem klasy pochodzącej od <xref:System.Exception?displayProperty=nameWithType>. W poniższym przykładzie użyto `throw` instrukcji throw <xref:System.IndexOutOfRangeException> Jeśli argument przekazany do metody o nazwie `GetNumber` nie odpowiada nieprawidłowy indeks tablicy wewnętrznej.

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Następnie użyj wywołań metody `try-catch` lub `try-catch-finally` bloku do obsługi zwrócony wyjątek. Poniższy przykład obsługi wyjątku zgłoszonego przez `GetNumber` metody.

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Ponownego generowania wyjątku

`throw`można również w `catch` bloku do ponownego zgłoszenia wyjątku jest obsługiwany w `catch` bloku.  W takim przypadku `throw` nie przyjmuje argumentu wyjątku. Jest najbardziej przydatne w przypadku metody przekazuje argumentu z obiekt wywołujący do innej metody w bibliotece, a metoda biblioteki zgłasza wyjątek, który musi być przekazywane do obiektu wywołującego. Na przykład poniższy przykład ponownie zgłasza <xref:System.NullReferenceException> zgłoszono podczas próby pobrania pierwszego znaku ciągu niezainicjowany. 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Można również użyć `throw e` składni w `catch` bloku można utworzyć nowy wyjątek, który jest przekazywany do obiektu wywołującego. W tym przypadku ślad stosu wyjątku oryginalnej, który jest dostępny z <xref:System.Exception.StackTrace> właściwości, nie są zachowywane.
 
## <a name="the-throw-expression"></a>`throw` Wyrażenia

Począwszy od C# 7, `throw` mogą być używane jako wyrażenie, a także instrukcję. Dzięki temu wyjątków w kontekstach, które były wcześniej obsługiwane. Należą do nich następujące elementy:

- [operator warunkowy](../operators/conditional-operator.md). W poniższym przykładzie użyto `throw` wyrażenie throw <xref:System.ArgumentException> Jeśli metoda jest przekazywana tablicy pusty ciąg. Przed C# 7, musi występować w tej logiki `if` / `else` instrukcji.

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [operator łączenie null](../operators/null-conditional-operator.md). W poniższym przykładzie `throw` wyrażenie jest używany z operatorem łączenie null zostać zgłoszony wyjątek, jeśli ciąg jest przypisany do `Name` jest właściwość `null`.
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- zabudowanych wyrażenie [lambda](../../lambda-expressions.md) lub metody. Poniższy przykład przedstawia zabudowanych wyrażenia metody, która zgłasza <xref:System.InvalidCastException> ponieważ konwersji na <xref:System.DateTime> wartość nie jest obsługiwana.
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Try, catch, a w języku C++ throw — instrukcje](../../../csharp/language-reference/keywords/try-catch.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Instrukcje obsługi wyjątków](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [Porady: jawne zgłaszanie wyjątków](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
