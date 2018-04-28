---
title: Operatory logiczne (F#)
description: 'Więcej informacji na temat operatorów logicznych, które są dostępne w języku programowania w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0b11b5133b02b6f507c7886b2fbaebf30abf46cb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="boolean-operators"></a>Operatory logiczne

W tym temacie opisano obsługę operatorów logicznych w języku F #.


## <a name="summary-of-boolean-operators"></a>Podsumowanie operatory logiczne
Poniższa tabela zawiera podsumowanie operatorów logicznych, które są dostępne w języku F #. Jest to jedyny typ obsługiwany przez te podmioty `bool` typu.

|Operator|Opis|
|--------|-----------|
|`not`|Logiczna Negacja|
|<code>&#124;&#124;</code>|Wartość logiczna lub|
|`&&`|Wartość logiczna AND|

Wykonaj logicznych AND i OR operatory *ocena zwarcia*, to znaczy umożliwiają podawanie wartości wyrażenie po prawej stronie operatora tylko w przypadku, gdy jest to niezbędne do obliczenia ogólnej wyniku wyrażenia. Drugie wyrażenie `&&` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `true`; drugie wyrażenie `||` operator jest oceniany, tylko, jeśli pierwsze wyrażenie daje w wyniku `false`.

## <a name="see-also"></a>Zobacz też
[Operatory bitowe](bitwise-operators.md)

[Operatory arytmetyczne](arithmetic-operators.md)

[Odwołanie do symboli i operatorów](index.md)
