---
title: "Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)
Ponieważ obiekt jest polimorficzny, istnieje możliwość zmiennej typu klasy podstawowej typu pochodnego. Aby uzyskać dostęp do metody typu pochodnego, należy rzutować wartości do typu pochodnego. Próba prostą rzutowanie w tych przypadkach tworzy jednak ryzyko zgłaszanie <xref:System.InvalidCastException>. Oznacza to dlaczego C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatorów. Aby sprawdzić, czy rzutowanie powiedzie się, nie powodując wyjątek zostanie wygenerowany, można użyć tych operatorów. Ogólnie rzecz biorąc `as` operator jest bardziej wydajne, ponieważ zwraca ono wartość rzeczywistą wartość rzutowania Jeśli rzutowanie może się pomyślnie. `is` Operator zwraca tylko wartość typu Boolean. W związku z tym można używać podczas po prostu chcesz określić typu obiektu, ale nie trzeba rzeczywistą rzutować go.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak używać `is` i `as` operatory rzutowania z jednego odwołania do typu na inny bez ryzyka Zgłaszanie wyjątku. W przykładzie przedstawiono również sposób użycia `as` operatora z typów wartości null.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md)
