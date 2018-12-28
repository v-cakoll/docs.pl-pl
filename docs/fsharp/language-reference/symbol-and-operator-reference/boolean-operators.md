---
title: Operatory logiczne
description: Dowiedz się więcej o operatorów logicznych, które są dostępne w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612741"
---
# <a name="boolean-operators"></a>Operatory logiczne

W tym temacie opisano obsługę operatorów logicznych w F# języka.

## <a name="summary-of-boolean-operators"></a>Podsumowanie operatory logiczne

Poniższa tabela zawiera podsumowanie operatorów logicznych, które są dostępne w F# języka. Jest to jedyny typ obsługiwanych przez te operatory `bool` typu.

|Operator|Opis|
|--------|-----------|
|`not`|Negacja logiczna|
|<code>&#124;&#124;</code>|Logiczne OR|
|`&&`|AND logiczne|

Logiczne AND i OR operatory wykonać *zwarcia*, czyli umożliwiają podawanie wartości wyrażenia po prawej stronie operatora tylko w przypadku, gdy jest to konieczne określić ogólny wynik wyrażenia. Drugie wyrażenie `&&` operator jest oceniane tylko wtedy, gdy pierwsze wyrażenie, które daje w wyniku `true`; drugie wyrażenie `||` operator jest oceniane tylko wtedy, gdy pierwsze wyrażenie, które daje w wyniku `false`.

## <a name="see-also"></a>Zobacz także

- [Operatory bitowe](bitwise-operators.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Odwołanie do symboli i operatorów](index.md)