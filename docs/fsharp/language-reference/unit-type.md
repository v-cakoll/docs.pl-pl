---
title: Typ jednostki (F#)
description: Dowiedz się, jak typ "jednostka" F# jest często używany do przechowywania to miejsce, w której wartość jest wymagana przez składnię języka żadnej wartości jest wymagane lub pożądane.
ms.date: 05/16/2016
ms.openlocfilehash: c3dfa5f63c25a1e8abc0f75b905c129b311479af
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "44204659"
---
# <a name="unit-type"></a>Typ jednostki

`unit` Typ to typ, który wskazuje brak określonej wartości; `unit` typ ma tylko jedną wartość, która działa jako symbolu zastępczego, gdy żadna inna wartość istnieje lub jest wymagana.

## <a name="syntax"></a>Składnia

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Uwagi

Każdy język F# wyrażenia musi być wartością. W wyrażeniach, które nie generują wartość, która ma znaczenie, wartości typu `unit` jest używany. `unit` Przypomina typu `void` typu w językach takich jak C# i C++.

`unit` Typ ma pojedynczą wartość, a ta wartość jest wskazywany przez token `()`.

Wartość `unit` typ jest często używany w języku F# programowania do przechowywania to miejsce, w przypadku, gdy wartość jest wymagana przez składnię języka, ale w przypadku, gdy wartość nie jest wymagane lub żądane. Przykładem może być wartość zwracaną przez `printf` funkcji. Ponieważ ważne akcje `printf` wykonać operacji w funkcji funkcji nie musi zwracać wartość rzeczywistą. W związku z tym, zwracana wartość jest typu `unit`.

Oczekiwać pewnych konstrukcji `unit` wartość. Na przykład `do` powiązania lub dowolnego kodu na najwyższym poziomie modułu powinien zwrócić `unit` wartość. Kompilator zgłosi ostrzeżenie podczas `do` powiązaniem lub kodem na najwyższym poziomie modułu daje wynik innych niż `unit` wartość, która nie jest używany, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

To ostrzeżenie jest to cecha programowania funkcjonalnego. nie ma w innych .NET, języków programowania. W programie czysto funkcjonalności, funkcje nie są wszelkie efekty uboczne końcowa wartość zwracana jest tylko wynik wywołania funkcji. W związku z tym gdy wynik jest ignorowane, jest możliwy błąd programowania. Chociaż F# nie jest całkowicie funkcjonalny język programowania, jest dobrym rozwiązaniem, postępuj zgodnie z funkcjonalności stylu programowania, jeśli to możliwe.

## <a name="see-also"></a>Zobacz także

- [Pierwotny](primitive-types.md)
- [Dokumentacja języka F#](index.md)
