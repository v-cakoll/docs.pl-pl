---
title: "gdy (odwołanie w C#)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords: when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f453d9f4b443d7adeeb0ab628b4ddad1a0116e49
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
 # <a name="when-c-reference"></a>gdy (odwołanie w C#)

Można użyć `when` kontekstowe słowo kluczowe do określenia warunku filtru w dwóch kontekstów:

- W `catch` instrukcja [bloku try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) bloku.
- W `case` etykietę [przełącznika](switch.md) instrukcji.

## <a name="when-in-a-catch-statement"></a>`when`w `catch` — instrukcja

Począwszy od języka C# 6, `When` mogą być używane w `catch` instrukcji do określenia warunku, który musi mieć wartość true dla programu obsługi dla określonego wyjątku do wykonania. Składnia to:

```csharp
catch ExceptionType [e] when (expr)
```
gdzie *wyrażenie* to wyrażenie, którego wynikiem jest wartość logiczna. Jeśli zmienna zwraca `true`, obsługa wyjątków wykonuje; Jeśli `false`, nie ma. 

W poniższym przykładzie użyto `when` — słowo kluczowe warunkowo wykonać obsługi <xref:System.Net.Http.HttpRequestException> w zależności od tekst komunikat o wyjątku.

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`when`w `switch` — instrukcja

Począwszy od 7, `case` etykiety już muszą być wykluczają się wzajemnie, a w kolejności `case` etykiety są wyświetlane w `switch` instrukcji można określić, który blok przełącznika wykonuje. `when` — Słowo kluczowe może służyć do określenia warunku filtru, który powoduje, że jego skojarzony etykiety case mieć wartość true tylko wtedy, gdy warunek filtru również ma wartość true. Składnia to:

```csharp
case (expr) when (when-condition):
```
gdzie *wyrażenie* jest stałe wzorzec lub wzorzec typu, który jest porównywany wyrażenie dopasowania i *warunek when* jest wyrażenia logicznego. 

W poniższym przykładzie użyto `when` — słowo kluczowe w celu zbadania `Shape` obiektów, które mają obszar zero, a także aby przetestować dla różnych `Shape` obiektów, które mają obszar większa od zera. 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>Zobacz także 
  [Switch — instrukcja](switch.md)  
  [try/catch — instrukcja](try-catch.md)  
  [instrukcji try/catch/finally](try-catch-finally.md) 

