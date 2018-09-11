---
title: gdy (odwołanie w C#)
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: a71cbdce256b1c1bd5d101d66f216fb229d70adf
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368378"
---
 # <a name="when-c-reference"></a>gdy (odwołanie w C#)

Możesz użyć `when` kontekstowe słowo kluczowe, aby określić warunek filtru w dwóch kontekstów:

- W `catch` instrukcja [bloku try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) bloku.
- W `case` etykieta [Przełącz](switch.md) instrukcji.

## <a name="when-in-a-catch-statement"></a>`when` w `catch` — instrukcja

Począwszy od C# 6, `When` mogą być używane w `catch` instrukcję, aby określić warunek, który musi mieć wartość true dla programu obsługi dla określonego wyjątku do wykonania. Jego składnia jest następująca:

```csharp
catch ExceptionType [e] when (expr)
```
gdzie *expr* jest wyrażeniem, którego wynikiem jest wartość typu Boolean. Jeśli zostanie zwrócona `true`, uruchamia program obsługi wyjątku; Jeśli `false`, nie ma. 

W poniższym przykładzie użyto `when` — słowo kluczowe warunkowo wykonanie procedury obsługi dla <xref:System.Net.Http.HttpRequestException> w zależności od tekstu komunikat o wyjątku.

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`when` w `switch` — instrukcja

Począwszy od C# 7.0, `case` etykiety już nie muszą być wzajemnie wyłącznie i kolejność, w której `case` etykiety pojawiają się w `switch` instrukcji można określić, które blok "switch" wykonuje. `when` — Słowo kluczowe może służyć do określania warunku filtru, który powoduje, że jego skojarzony etykiety case PRAWDA, tylko wtedy, gdy warunek filtru jest również wartość true. Jego składnia jest następująca:

```csharp
case (expr) when (when-condition):
```
gdzie *expr* wzór stałej lub wzorzec typ, który jest porównywany z wyrażenie dopasowania i *kiedy warunek* jest dowolne wyrażenie logiczne. 

W poniższym przykładzie użyto `when` — słowo kluczowe do testowania `Shape` obiektów, które mają obszar o wartości zero, a także do testowania różnych `Shape` obiektów, które mają obszar jest większy od zera. 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>Zobacz także

- [Switch — instrukcja](switch.md)  
- [Instrukcja try/catch](try-catch.md)  
- [instrukcji try/catch/finally](try-catch-finally.md) 
