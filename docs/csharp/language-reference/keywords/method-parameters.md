---
title: Parametry metody (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 8a8d300661eec42030900dd9ee85a17e66aa0922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="method-parameters-c-reference"></a>Parametry metody (odwołanie w C#)

Zadeklarowane parametry dla metody bez [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md), są przekazywane do metody wywoływane przez wartość. Tę wartość można zmienić w metodzie, ale zmiany wartości nie zostaną zachowane, gdy formant przechodzi do procedury wywołującej. Za pomocą słowa kluczowego parametru metody, można zmienić to zachowanie.  
  
 W tej sekcji opisano słowa kluczowe, które można użyć przy deklarowaniu parametry metody:  
  
-   [Parametry](../../../csharp/language-reference/keywords/params.md) Określa, że ten parametr może zostać zmienną liczbę argumentów.
  
-   [w](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Określa, że ten parametr jest przekazywany przez odwołanie, ale jest tylko do odczytu przez metodę o nazwie.
  
-   [REF](../../../csharp/language-reference/keywords/ref.md) Określa, że ten parametr jest przekazywany przez odwołanie i może odczytu lub zapisu przez metodę o nazwie.
  
-   [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Określa, że ten parametr jest przekazywany przez odwołanie i są zapisywane przez metodę o nazwie.
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
