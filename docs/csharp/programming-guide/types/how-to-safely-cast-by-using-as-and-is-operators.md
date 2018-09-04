---
title: 'Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 8e0b17122bd23a7de82ca1c210a559fe09ad7fee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508121"
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>Porady: bezpieczne rzutowanie za pomocą operatorów as i is (Przewodnik programowania w języku C#)
Ponieważ obiekty są polimorficznych, jest możliwe dla zmiennej do przechowywania Typ pochodny typ klasy bazowej. Aby uzyskać dostęp do metod wystąpienia typu pochodnego, jest niezbędne Rzutowanie wartości do typu pochodnego. Próby prostego rzutowanie w tych przypadkach tworzy jednak ryzyko zgłaszanie <xref:System.InvalidCastException>. Oznacza to dlaczego C# zawiera [jest](../../../csharp/language-reference/keywords/is.md) i [jako](../../../csharp/language-reference/keywords/as.md) operatorów. Te operatory służy do sprawdzenia, czy rzutowania powiedzie się bez powodowania zgłoszenie wyjątku. Ogólnie rzecz biorąc `as` operator jest bardziej wydajne, ponieważ faktycznie program zwraca wartość rzutowania w przypadku rzutowania może się pomyślnie. `is` Operator zwraca tylko wartość typu Boolean. Można w związku z tym używane, gdy po prostu chcesz określić typu obiektu, ale nie trzeba go rzutować faktycznie.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano sposób użycia `is` i `as` operatorów rzutowania z jedno odwołanie do typu na inny bez ryzyka zostanie zgłoszony wyjątek. W przykładzie pokazano również sposób użycia `as` operatora z typami wartości null.  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Typy](../../../csharp/programming-guide/types/index.md)  
- [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [Typy dopuszczające wartości null](../../../csharp/programming-guide/nullable-types/index.md)
