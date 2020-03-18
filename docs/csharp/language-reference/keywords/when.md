---
title: gdy kontekstowe słowo kluczowe — odwołanie do języka C#
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712835"
---
# <a name="when-c-reference"></a>kiedy (Odwołanie do Języka C#)

Można użyć `when` kontekstowesłowo kluczowe, aby określić warunek filtru w dwóch kontekstach:

- W `catch` instrukcji [try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) bloku.
- W `case` etykiecie [instrukcji switch.](switch.md)

## <a name="when-in-a-catch-statement"></a>`when`w `catch` oświadczeniu

Począwszy od języka `when` C# 6, może służyć w `catch` instrukcji, aby określić warunek, który musi być true dla programu obsługi dla określonego wyjątku do wykonania. Jego składnia jest:

```csharp
catch (ExceptionType [e]) when (expr)
```

gdzie *expr* jest wyrażeniem, które oblicza wartość logiczną. Jeśli zwraca `true`, program obsługi wyjątków wykonuje; jeśli `false`, nie.

W poniższym `when` przykładzie użyto słowa kluczowego <xref:System.Net.Http.HttpRequestException> do warunkowo wykonywania programów obsługi dla w zależności od tekstu komunikatu o wyjątku.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when`w `switch` oświadczeniu

Począwszy od języka C# 7.0, etykiety nie muszą `case` się wzajemnie `switch` wykluczać, a kolejność, w jakiej etykiety pojawiają się w instrukcji można określić, `case` który blok przełącznika wykonuje. Słowo `when` kluczowe może służyć do określenia warunku filtru, który powoduje, że jego skojarzona etykieta sprawy jest true tylko wtedy, gdy warunek filtru jest również true. Jego składnia jest:

```csharp
case (expr) when (when-condition):
```

gdzie *expr* jest stały wzorzec lub wzorzec typu, który jest porównywany do wyrażenia dopasowania, a *gdy warunek* jest dowolne wyrażenie logiczne.

W poniższym `when` przykładzie użyto `Shape` słowa kluczowego do testowania obiektów, które mają `Shape` obszar zero, a także do testowania dla różnych obiektów, które mają obszar większy niż zero.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Zobacz też

- [instrukcja switch](switch.md)
- [instrukcja try/catch](try-catch.md)
- [instrukcja try/catch/finally](try-catch-finally.md)
