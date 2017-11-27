---
title: Operatory logiczne (F#)
description: "Więcej informacji na temat operatorów logicznych, które są dostępne w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

[Operator odwołanie do symbolu i](index.md)
