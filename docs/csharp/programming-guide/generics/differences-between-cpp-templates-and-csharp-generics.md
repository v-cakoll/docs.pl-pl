---
title: Różnice między szablonami C++ i C# typów ogólnych — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: 1bf3eb97d633322f6bd04f8e975ae3fc8ec54329
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651813"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Różnice między szablonami C++ i typami ogólnymi C# (Przewodnik programowania w języku C#)
Szablony typami ogólnymi C# i C++ są obie funkcje językowe, pozwalające na obsługę typów sparametryzowanych. Istnieją jednak wiele różnic między nimi. Na poziomie składni typami ogólnymi C# są prostsze sparametryzowanych typów bez złożoność szablonów języka C++. Ponadto C# nie próbuje zapewniają wszystkich funkcji, które zapewniają szablonów języka C++. Na poziomie wdrożenia główną różnicą jest, że podstawienia typu ogólnego C# są wykonywane w czasie wykonywania i informacje o typie ogólny, tym samym są zachowywane do wystąpień obiektów. Aby uzyskać więcej informacji, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Poniżej przedstawiono podstawowe różnice między typami ogólnymi C# i szablonów języka C++:  
  
-   Typami ogólnymi C# nie są oferowane tyle samo elastyczność jako szablonów języka C++. Na przykład prawdopodobnie nie wywoła operatorów arytmetycznych w języku C# klasy ogólnej, chociaż jest możliwe do wywołania operatory zdefiniowane przez użytkownika.  
  
-   C# nie zezwala na parametrów szablonu bez typu, takie jak `template C<int i> {}`.  
  
-   C# nie obsługuje jawna specjalizacja; oznacza to, że implementacja niestandardowa szablonu dla określonego typu.  
  
-   C# nie obsługuje częściowej specjalizacji: implementacja niestandardowa dla podzbioru argumentów typu.  
  
-   C# nie zezwala na parametr typu ma być używany jako klasa bazowa dla typu ogólnego.  
  
-   C# nie zezwala na parametry typu mają domyślne typy.  
  
-   W języku C#, parametru typu generycznego nie może sam być ogólnego, chociaż typy utworzone mogą być używane jako ogólne. C++ umożliwia parametry szablonu.  
  
-   C++ umożliwia kod, który nie jest prawidłowe dla wszystkich parametrów typu w szablonie, które następnie są sprawdzane pod kątem określonego typu, używany jako parametr typu. Język C# wymaga kod w klasie do zapisania w taki sposób, że będzie ona współdziałać z dowolnego typu, który spełnia ograniczenia. Na przykład w języku C++ istnieje możliwość pisania funkcji, która używa operatorów arytmetycznych `+` i `-` obiektów parametr typu, która powoduje wygenerowanie błędu w momencie konkretyzacji szablonu o typie, który nie obsługuje tych operatory. C# nie zezwalają na to; konstrukcji języka tylko dozwolone są te, które wynikają z ograniczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [Szablony](/cpp/cpp/templates-cpp)
