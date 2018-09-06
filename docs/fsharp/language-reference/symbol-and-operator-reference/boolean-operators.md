---
title: Operatory logiczne (F#)
description: 'Więcej informacji na temat operatorów logicznych, które są dostępne w F # języka programowania.'
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784517"
---
# <a name="boolean-operators"></a>Operatory logiczne

W tym temacie opisano obsługę operatorów logicznych w języku F #.

## <a name="summary-of-boolean-operators"></a>Podsumowanie operatory logiczne

Poniższa tabela zawiera podsumowanie operatorów logicznych, które są dostępne w języku F #. Jest to jedyny typ obsługiwanych przez te operatory `bool` typu.

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
