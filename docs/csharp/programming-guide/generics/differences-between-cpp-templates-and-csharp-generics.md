---
title: Różnice między szablonami C++ i generykami Języka C# — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
ms.openlocfilehash: e44f67353410c58c406620109270972df17f9f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703536"
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a>Różnice między szablonami C++ i typami ogólnymi C# (Przewodnik programowania w języku C#)
C# Generics i C++ szablony są zarówno funkcje języka, które zapewniają obsługę typów sparametryzowanych. Istnieje jednak wiele różnic między nimi. Na poziomie składni generycznych C# są prostsze podejście do typów sparametryzowanych bez złożoności szablonów C++. Ponadto C# nie próbuje zapewnić wszystkie funkcje, które zapewniają szablony Języka C++. Na poziomie implementacji podstawową różnicą jest to, że substytucje typów ogólnych języka C# są wykonywane w czasie wykonywania, a informacje o typie ogólnym są zachowywane dla obiektów wystąpienia. Aby uzyskać więcej informacji, zobacz [Ogólne w czasie wykonywania](./generics-in-the-run-time.md).  
  
 Poniżej przedstawiono kluczowe różnice między szablonami C# Generics i C++:  
  
- Generykczna języka C# nie zapewniają taką samą elastyczność jak szablony Języka C++. Na przykład nie jest możliwe wywołanie operatorów arytmetycznych w klasie ogólnej Języka C#, chociaż można wywołać operatory zdefiniowane przez użytkownika.  
  
- C# nie zezwala na parametry szablonu `template C<int i> {}`nietypu, takie jak .  
  
- C# nie obsługuje jawnej specjalizacji; oznacza to, że implementacja niestandardowa szablonu dla określonego typu.  
  
- C# nie obsługuje częściowej specjalizacji: implementacja niestandardowa dla podzbioru argumentów typu.  
  
- C# nie zezwala na parametr typu, który ma być używany jako klasa podstawowa dla typu ogólnego.  
  
- C# nie zezwala na parametry typu mają typy domyślne.  
  
- W języku C#, parametr typu ogólnego sam nie może być rodzajowy, chociaż typy konstruowane mogą służyć jako generycznych. C++ zezwala na parametry szablonu.  
  
- C++ umożliwia kod, który może nie być prawidłowy dla wszystkich parametrów typu w szablonie, który jest następnie sprawdzany dla określonego typu używanego jako parametr typu. C# wymaga kodu w klasie, które mają być napisane w taki sposób, że będzie działać z dowolnego typu, który spełnia ograniczenia. Na przykład w języku C++ można napisać funkcję, która `+` używa `-` operatorów arytmetycznych i obiektów parametru typu, który spowoduje błąd w momencie wystąpienia szablonu z typem, który nie obsługuje tych operatorów. C# nie zezwala na to; tylko konstrukcje języka dozwolone są te, które można wywnioskować z ograniczeń.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Szablony](/cpp/cpp/templates-cpp)
