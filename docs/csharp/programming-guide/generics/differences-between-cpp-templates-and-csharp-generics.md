---
title: Różnice między szablonami C++ i typami ogólnymi C# (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: db3311c7fa81d48137c542f320d0abef791e5116
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Różnice między szablonami C++ i typami ogólnymi C# (Przewodnik programowania w języku C#)
Szablony typami ogólnymi C# i C++ są obie funkcje języka, które obsługują typy z parametrami. Istnieje jednak wiele różnice między nimi. Na poziomie składni typami ogólnymi C# są prostsze typom sparametryzowane bez złożoności szablonów języka C++. Ponadto C# nie podejmowana próba udostępnienia wszystkie funkcje, które zapewniają szablonów języka C++. Na poziomie implementacji podstawowa różnica polega na podstawienia typu ogólnego C# są wykonywane w czasie wykonywania, a informacje o typie ogólnym co są zachowywane dla wystąpień obiektów. Aby uzyskać więcej informacji, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Poniżej przedstawiono podstawowe różnice między szablony C++ i typami ogólnymi C#:  
  
-   Typami ogólnymi C# nie udostępniają samo elastyczność jako szablonów języka C++. Na przykład go nie jest możliwe do wywołania operatorów arytmetycznych w języku C# klasy ogólnej, chociaż można wywołać operatory zdefiniowane przez użytkownika.  
  
-   C# nie zezwala na parametry szablonu bez typu, takich jak `template C<int i> {}`.  
  
-   C# nie obsługuje jawnej specjalizacji; oznacza to, że implementacja niestandardowa szablonu dla określonego typu.  
  
-   C# nie obsługuje częściowa specjalizacja: implementacja niestandardowa dla podzbioru argumentów typu.  
  
-   C# nie zezwala na parametr typu do użycia jako klasę podstawową dla typu ogólnego.  
  
-   C# nie zezwala na parametry typu mają domyślnych typów.  
  
-   W języku C#, parametru typu ogólnego nie może sam być ogólnego, chociaż typy utworzone mogą być używane jako ogólne. Zezwalaj na C++ parametrów szablonu.  
  
-   C++ pozwala kod, który nie jest prawidłowe dla wszystkich parametrów typu w szablonie, który następnie jest sprawdzany pod kątem określonego typu użyć jako parametru typu. C# wymaga kod w klasie, do zapisania w taki sposób, że będzie ona działać w przypadku każdego typu spełniającego ograniczenia. Na przykład w języku C++ istnieje możliwość zapisu funkcję, która używa operatorów arytmetycznych `+` i `-` na obiektach parametr typu, który utworzy wystąpił błąd w czasie tworzenia wystąpienia szablonu z typem, który nie obsługuje te operatory. C# nie są dozwolone. konstrukcji języka tylko dozwolone są tymi, które wynikają z ograniczeniami.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Szablony](/cpp/cpp/templates-cpp)
