---
title: Parametry metody (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 446a5239fa1de8559dea50f7e8b8869aed0297c5
ms.sourcegitcommit: 875ecc3ab2437e299b1d50076bd9b878fa8c64de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43238498"
---
# <a name="method-parameters-c-reference"></a>Parametry metody (odwołanie w C#)

Parametry zadeklarowane dla metody bez [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md), są przekazywane do metody wywoływane przez wartość. Tę wartość można zmienić w metodzie, ale zmiany wartości nie zostaną zachowane, gdy kontrola przechodzi do procedury wywołującej. Za pomocą słowo kluczowe parametru metody, można zmienić to zachowanie.  
  
 W tej sekcji opisano słowa kluczowe, których można użyć podczas deklarowania parametry metody:  
  
-   [params](../../../csharp/language-reference/keywords/params.md) Określa, że ten parametr może potrwać zmienną liczbę argumentów.
  
-   [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Określa, że ten parametr jest przekazywany przez odwołanie, ale jest odczytywany tylko przez metodę o nazwie.
  
-   [REF](../../../csharp/language-reference/keywords/ref.md) Określa, że ten parametr jest przekazywany przez odwołanie i może być odczytywanych lub zapisywanych przez metodę o nazwie.
  
-   [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Określa, że ten parametr jest przekazywany przez odwołanie i są zapisywane przez metodę o nazwie.
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
