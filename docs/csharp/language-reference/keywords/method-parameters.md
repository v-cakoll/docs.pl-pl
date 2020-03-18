---
title: Parametry metody — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 2cc7f9178fa5c1a040be9d45ba66fac292bb0e28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713374"
---
# <a name="method-parameters-c-reference"></a>Parametry metody (odwołanie w C#)

Parametry zadeklarowane dla metody bez [w](./in-parameter-modifier.md), [ref](./ref.md) lub [out](./out-parameter-modifier.md), są przekazywane do metody wywoływanej przez wartość. Tę wartość można zmienić w metodzie, ale zmieniona wartość nie zostanie zachowana, gdy kontrola przechodzi z powrotem do procedury wywoływania. Za pomocą słowa kluczowego parametrmetody można zmienić to zachowanie.  
  
 W tej sekcji opisano słowa kluczowe, których można użyć podczas deklarowania parametrów metody:  
  
- [params](./params.md) określa, że ten parametr może mieć zmienną liczbę argumentów.
  
- [w](./in-parameter-modifier.md) określa, że ten parametr jest przekazywany przez odwołanie, ale jest odczytywany tylko przez wywoływana metoda.
  
- [ref](./ref.md) określa, że ten parametr jest przekazywany przez odwołanie i może być odczytywany lub zapisywany przez wywoływaną metodę.
  
- [out](./out-parameter-modifier.md) określa, że ten parametr jest przekazywany przez odwołanie i jest zapisywany przez wywoływaną metodę.
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
