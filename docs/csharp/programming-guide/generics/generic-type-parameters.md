---
title: Parametry typu ogólnego - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 48fa90226b7a8a36f5f432921cf5d999e76c6fa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681641"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parametry typu ogólnego (Przewodnik programowania w języku C#)
W ogólnym typie lub definicję metody parametry typu jest symbolem zastępczym dla określonego typu, że klient określa podczas ich tworzenia wystąpienia zmienną typu rodzajowego. Klasy ogólnej, takich jak `GenericList<T>` na liście [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md), nie można użyć jako — ponieważ nie jest tak naprawdę typu; więcej podobna do planu dla typu. Aby użyć `GenericList<T>`, kod klienta należy zadeklarować i tworzenia wystąpienia typu skonstruowany, określając argument typu w nawiasach ostrych. Typ argumentu dla tej konkretnej klasy mogą być dowolnego typu, rozpoznawane przez kompilator. Dowolną liczbę wystąpień skonstruowanego typu mogą być tworzone, każdy z nich przy użyciu argumentu innego typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 W każdym z tych wystąpień `GenericList<T>`, każde wystąpienie `T` w klasie, zostaną zastąpione w czasie wykonywania z argumentem typu. Za pomocą tego podstawienia przygotowaliśmy trzy oddzielne obiekty bezpieczny i efektywny przy użyciu definicji pojedynczą klasę. Aby uzyskać więcej informacji na temat sposobu to zastąpienie jest wykonywane przez środowisko CLR, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Parametr typu wskazówki dotyczące nazewnictwa  
  
-   **Czy** nazw parametrów typu ogólnego przy użyciu nazw opisowych, chyba, że nazwa pojedynczą literą jest całkowicie własnym objaśniający i nazwę opisową nie wprowadziłaby dodatkowej wartości.  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Należy wziąć pod uwagę** przy użyciu języka T jako nazwę parametru typu dla typów, z jednym parametrem typu pojedynczą literą.  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Czy** prefiks nazwy parametrów typu opisowy z "T".  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Należy wziąć pod uwagę** wskazujący ograniczenia umieścić w parametrze typu nazwę parametru. Na przykład parametr ograniczone do `ISession` może być wywołana `TSession`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Typy ogólne](../../../csharp/programming-guide/generics/index.md)
- [Różnice między szablonami C++ i typami ogólnymi C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
