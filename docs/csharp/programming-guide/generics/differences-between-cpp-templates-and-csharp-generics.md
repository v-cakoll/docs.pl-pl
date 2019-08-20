---
title: Różnice między C++ szablonami C# i ogólnymi C# przewodnikami programistycznymi
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: b794666501fb27d2f73a6050f85df3725050982e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589854"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Różnice między szablonami C++ i typami ogólnymi C# (Przewodnik programowania w języku C#)
C#Typy ogólne i C++ szablony są funkcjami językowymi, które zapewniają obsługę typów sparametryzowanych. Istnieje jednak wiele różnic między nimi. Na poziomie składni C# generyczne są prostsze podejścia do typów sparametryzowanych bez złożoności C++ szablonów. Ponadto program C# nie podejmuje próby udostępnienia wszystkich funkcji udostępnianych przez C++ szablony. Na poziomie implementacji podstawowa różnica polega na tym, że C# podstawienia typów ogólnych są wykonywane w czasie wykonywania, a ogólne informacje o typie są zachowywane w przypadku obiektów wystąpień. Aby uzyskać więcej informacji, zobacz [typy ogólne w czasie wykonywania](./generics-in-the-run-time.md).  
  
 Poniżej przedstawiono kluczowe różnice między C# ogólnymi i C++ szablonami:  
  
- C#typy ogólne nie zapewniają takiej samej elastyczności jak C++ szablony. Na przykład nie jest możliwe wywołanie operatorów arytmetycznych w klasie C# generycznej, chociaż istnieje możliwość wywołania operatorów zdefiniowanych przez użytkownika.  
  
- C#nie zezwala na parametry szablonu bez typu, takie jak `template C<int i> {}`.  
  
- C#nie obsługuje jawnej specjalizacji; oznacza to, że niestandardowa implementacja szablonu dla określonego typu.  
  
- C#nie obsługuje specjalizacji częściowej: niestandardowej implementacji dla podzbioru argumentów typu.  
  
- C#nie zezwala na użycie parametru typu jako klasy bazowej dla typu ogólnego.  
  
- C#nie zezwala na parametry typu mające typy domyślne.  
  
- W C#programie parametr typu generycznego nie może być typem ogólnym, chociaż skonstruowane typy mogą służyć jako generyczne. C++zezwala na parametry szablonu.  
  
- C++zezwala na kod, który może być nieprawidłowy dla wszystkich parametrów typu w szablonie, który jest sprawdzany pod kątem określonego typu, który jest używany jako parametr typu. C#wymaga, aby kod w klasie był pisany w taki sposób, że będzie działał z dowolnym typem, który spełnia ograniczenia. Na przykład C++ można napisać funkcję, która używa operatorów `+` arytmetycznych i `-` obiektów parametru typu, co spowoduje błąd w czasie tworzenia wystąpienia szablonu z typem, który nie Obsługuj te operatory. C#nie zezwala na to; Jedyne konstrukcje języka dozwolone są te, które można wywnioskować na podstawie ograniczeń.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Szablony](/cpp/cpp/templates-cpp)
