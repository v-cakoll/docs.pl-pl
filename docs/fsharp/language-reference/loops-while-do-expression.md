---
title: "Pętle: while...do — Wyrażenie (F#)"
description: "Zobacz temat jak podczas... czy wyrażenie jest używana do wykonywania iteracji wykonywania (zapętlenia), podczas testu określony warunek jest spełniony."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 5f10fda84a5e748856eb7b2c63ad46cc1fba44bb
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="loops-whiledo-expression"></a>Pętle: while...do — Wyrażenie

`while...do` Wyrażenie służy do wykonywania iteracji wykonywania (zapętlenia), podczas testu określony warunek jest spełniony.


## <a name="syntax"></a>Składnia

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Uwagi
*Testu wyrażenie* jest oceniany; Jeśli `true`, *treść wyrażenia* jest wykonywany i ponownie obliczyć wyrażenia testu. *Treść wyrażenia* musi mieć typ `unit`. Jeśli wyrażenie testu jest `false`, zakończenia iteracji.

Poniższy przykład przedstawia użycie `while...do` wyrażenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Dane wyjściowe poprzedniego kodu jest strumień losowych liczb od 1 do 20, ostatni wynosi 10.

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
Można użyć `while...do` w wyrażeniach sekwencji i inne wyrażenia obliczeń, w którym to przypadku dostosowaną wersję `while...do` wyrażenie jest używane. Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md), [Asynchroniczne przepływy pracy](asynchronous-workflows.md), i [wyrażenia obliczeń](computation-expressions.md).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)

[Pętle: `for...in` wyrażenia](loops-for-in-expression.md)

[Pętle: `for...to` wyrażenia](loops-for-to-expression.md)
