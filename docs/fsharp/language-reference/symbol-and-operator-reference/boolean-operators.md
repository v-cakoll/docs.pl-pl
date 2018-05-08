---
title: Operatory logiczne (F#)
description: 'Więcej informacji na temat operatorów logicznych, które są dostępne w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
