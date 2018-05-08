---
title: 'Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 6e02675a2a895add245d3c2e40305a0417fdf429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)
Ponieważ obiekt jest polimorficzny, istnieje możliwość zmiennej typu klasy podstawowej typu pochodnego. Aby uzyskać dostęp do metody typu pochodnego, należy rzutować wartości do typu pochodnego. Próba prostą rzutowanie w tych przypadkach tworzy jednak ryzyko zgłaszanie <xref:System.InvalidCastException>. Oznacza to dlaczego C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatorów. Aby sprawdzić, czy rzutowanie powiedzie się, nie powodując wyjątek zostanie wygenerowany, można użyć tych operatorów. Ogólnie rzecz biorąc `as` operator jest bardziej wydajne, ponieważ zwraca ono wartość rzeczywistą wartość rzutowania Jeśli rzutowanie może się pomyślnie. `is` Operator zwraca tylko wartość typu Boolean. W związku z tym można używać podczas po prostu chcesz określić typu obiektu, ale nie trzeba rzeczywistą rzutować go.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać `is` i `as` operatory rzutowania z jednego odwołania do typu na inny bez ryzyka Zgłaszanie wyjątku. W przykładzie przedstawiono również sposób użycia `as` operatora z typów wartości null.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)
