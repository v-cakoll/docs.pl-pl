---
title: Typ jednostki
description: Dowiedz się F# , w jaki sposób typ "Unit" jest często używany do przechowywania wartości wymaganej przez składnię języka, gdy wartość nie jest potrzebna lub nie jest wymagana.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630177"
---
# <a name="unit-type"></a>Typ jednostki

Typ jest typem, który wskazuje brak określonej wartości `unit` ; typ ma tylko jedną wartość, która działa jako symbol zastępczy, gdy inna wartość nie istnieje lub nie jest wymagana. `unit`

## <a name="syntax"></a>Składnia

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Uwagi

Każde F# wyrażenie musi być szacowane do wartości. W przypadku wyrażeń, które nie generują wartości będącej przedmiotem zainteresowania, używana jest wartość `unit` typu. Typ `unit` jest podobny do `void` typu w językach, takich jak C# i C++.

Typ ma pojedynczą wartość, a ta wartość jest wskazywana przez token `()`. `unit`

Wartość `unit` typu jest często używana w F# programowaniu do przechowywania miejsca, w którym wartość jest wymagana przez składnię języka, ale gdy wartość nie jest potrzebna lub nie jest wymagana. Przykładem może być wartość `printf` zwracana przez funkcję. Ponieważ ważne akcje `printf` operacji są wykonywane w funkcji, funkcja nie musi zwracać wartości rzeczywistej. W związku z tym wartość zwracana jest typu `unit`.

Niektóre konstrukcje oczekują `unit` wartości. Na przykład, `do` oczekiwane jest powiązanie lub dowolny kod na najwyższym poziomie modułu, który ma zostać obliczony `unit` do wartości. Kompilator zgłasza ostrzeżenie, gdy `do` powiązanie lub kod na najwyższym poziomie modułu generuje wynik inny `unit` niż wartość, która nie jest używana, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

To ostrzeżenie jest cechą programowania funkcjonalnego; nie jest ona wyświetlana w innych językach programowania .NET. W czystym programie funkcjonalnym, w którym funkcje nie mają żadnych efektów ubocznych, końcowa wartość zwracana jest jedynym wynikiem wywołania funkcji. W związku z tym, gdy wynik jest ignorowany, jest to możliwy błąd programowania. Chociaż F# nie jest to czysto funkcjonalny język programowania, dobrym sposobem jest przestrzeganie stylu programowania funkcjonalnego, jeśli jest to możliwe.

## <a name="see-also"></a>Zobacz także

- [Podstawowy](primitive-types.md)
- [Dokumentacja języka F#](index.md)
