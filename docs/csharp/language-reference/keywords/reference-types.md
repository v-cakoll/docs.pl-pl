---
title: "Typy odwołań (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4f87363246deccf282b499aa2afee2a14d41593
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reference-types-c-reference"></a>Typy odwołań (odwołanie w C#)
Istnieją dwa rodzaje typów w języku C#: typy referencyjne i typy wartości. W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane. W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna. Z typami wartość każdej zmiennej ma własną kopię danych, a nie jest możliwe w dla operacji na jedną zmienną do wpływu na drugi (z wyjątkiem w przypadku ref i out parametru zmiennych, zobacz [ref](../../../csharp/language-reference/keywords/ref.md) i [parametru out Modyfikator](../../../csharp/language-reference/keywords/out-parameter-modifier.md)).  
  
 Do deklarowania typów referencyjnych są używane następujące słowa kluczowe:  
  
-   [klasy](../../../csharp/language-reference/keywords/class.md)  
  
-   [Interfejs](../../../csharp/language-reference/keywords/interface.md)  
  
-   [Delegowanie](../../../csharp/language-reference/keywords/delegate.md)  
  
 W języku C# są także dostępne następujące wbudowane typy referencyjne:  
  
-   [dynamiczne](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [obiekt](../../../csharp/language-reference/keywords/object.md)  
  
-   [ciąg](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)
