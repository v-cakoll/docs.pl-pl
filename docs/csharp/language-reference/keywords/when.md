---
title: gdy kontekstowe słowo C# kluczowe-odwołanie
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712835"
---
# <a name="when-c-reference"></a>When (C# odwołanie)

Możesz użyć słowa kluczowego `when` kontekstowego, aby określić warunek filtru w dwóch kontekstach:

- W instrukcji `catch` bloku [try/catch](try-catch.md) lub [try/catch/finally](try-catch-finally.md) .
- W etykiecie `case` instrukcji [Switch](switch.md) .

## <a name="when-in-a-catch-statement"></a>`when` w instrukcji `catch`

Począwszy od C# 6, `when` może być użyty w instrukcji `catch`, aby określić warunek, który musi mieć wartość true dla programu obsługi określonego wyjątku do wykonania. Jego składnia to:

```csharp
catch (ExceptionType [e]) when (expr)
```

gdzie *Expr* jest wyrażeniem, którego wynikiem jest wartość logiczna. Jeśli zwróci `true`, program obsługi wyjątków zostanie wykonany; Jeśli `false`, nie jest.

Poniższy przykład używa słowa kluczowego `when`, aby warunkowo wykonywać procedury obsługi dla <xref:System.Net.Http.HttpRequestException> w zależności od tekstu komunikatu o wyjątku.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when` w instrukcji `switch`

Począwszy od C# 7,0, etykiety `case` nie muszą już być wykluczane wzajemnie, a kolejność, w której `case` etykiety pojawiają się w instrukcji `switch` może ustalić, który blok przełącznika jest wykonywany. Za pomocą słowa kluczowego `when` można określić warunek filtru, który powoduje, że skojarzona z nim etykieta Case ma wartość true tylko wtedy, gdy warunek filtru ma również wartość true. Jego składnia to:

```csharp
case (expr) when (when-condition):
```

gdzie *Expr* jest wzorcem stałej lub wzorcem typu, który jest porównywany z wyrażeniem Match, a *warunek when* jest dowolnym wyrażeniem logicznym.

Poniższy przykład używa słowa kluczowego `when` do testowania `Shape` obiektów, które mają powierzchnię zero, a także do testowania dla różnych `Shape` obiektów, które mają obszar większy niż zero.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Zobacz także

- [Switch, instrukcja](switch.md)
- [Instrukcja try/catch](try-catch.md)
- [Instrukcja try/catch/finally](try-catch-finally.md)
