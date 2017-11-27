---
title: Typ jednostki (F#)
description: "Dowiedz się, jak typu \"unit\" F # jest często używane do przechowywania w miejscu, gdzie wartość jest wymagana przez składni języka żadnej wartości jest wymagane lub pożądane."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: eabbb6d7-80f3-4fa5-80b4-0f48982466a7
ms.openlocfilehash: 60ac08c0e3f8380a8f9dec7a083ede93c68bb0e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unit-type"></a>Typ jednostki

`unit` Typ jest typem, który wskazuje brak określonej wartości; `unit` typ ma tylko jedną wartość, który działa jako symbol zastępczy, gdy żadna inna wartość istnieje lub jest wymagana.


## <a name="syntax"></a>Składnia

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a>Uwagi
Każdy F # wyrażenia musi być wartością. Dla wyrażeń, które nie generują wartość, która ma znaczenie, wartość typu `unit` jest używany. `unit` Podobny typ `void` typu w językach takich jak C# i C++.

`unit` Pojedynczą wartość ma typ, a ta wartość jest wskazywana przez token `()`.

Wartość `unit` typ jest często używany w języku F # programowania do przechowywania miejsce w przypadku, gdy wartość jest wymagana przez składni języka, ale w przypadku, gdy żadna wartość jest wymagane lub pożądane. Przykładem może być zwracana wartość `printf` funkcji. Ponieważ ważne działania `printf` wykonać operacji w funkcji funkcji nie musi zwracać wartość rzeczywistą. W związku z tym jest zwracana wartość typu `unit`.

Niektóre konstrukcje oczekiwać `unit` wartość. Na przykład `do` binding lub dowolny kod na najwyższym poziomie modułu powinien zwrócić `unit` wartość. Kompilator zgłosi ostrzeżenie podczas `do` powiązanie lub kod na najwyższym poziomie modułu powstaje innych niż `unit` wartość, która nie jest używany, jak pokazano w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

To ostrzeżenie jest to cecha programowanie funkcjonalne; nie ma w innych .NET języków programowania. W programie czysto funkcjonalności, funkcje nie są wszystkie efekty uboczne końcowej zwracany jest jedynym wynikiem wywołania funkcji. W związku z tym gdy wynik jest ignorowane, jest możliwy błąd programowania. Chociaż F # nie jest całkowicie funkcjonalny język programowania, jest dobrą praktyką jest wykonaj funkcjonalności styl programowania, jeśli to możliwe.

## <a name="see-also"></a>Zobacz też
[Pierwotne](primitive-types.md)

[Dokumentacja języka F #](index.md)
