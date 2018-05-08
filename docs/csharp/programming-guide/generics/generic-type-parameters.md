---
title: Parametry typu ogólnego (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 35029b90fb7b905a87055596cf8dcd6a84ef9d36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parametry typu ogólnego (Przewodnik programowania w języku C#)
W ogólnym typie lub metoda definicji parametry typu jest symbolem zastępczym dla klienta określa, po ich wystąpienia zmiennej typu ogólnego określonego typu. Klasy ogólnego, takich jak `GenericList<T>` na liście [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md), nie można użyć jako — ponieważ nie jest naprawdę typu, lecz więcej podobny do planu dla typu. Aby użyć `GenericList<T>`, kod klienta należy zadeklarować i tworzenia wystąpienia typu utworzone przez określenie argumentu typu w nawiasach ostrych. Typ argumentu dla tej konkretnej klasy mogą być dowolnego typu, rozpoznany przez kompilator. Dowolną liczbę wystąpień skonstruowanego typu mogą być tworzone, każda z nich przy użyciu argumentu innego typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]  
  
 W każdym z tych wystąpień `GenericList<T>`, każde wystąpienie `T` klasy zostaną zastąpione w czasie wykonywania z argumentem typu. Za pomocą tego podstawienia utworzono trzech oddzielnych obiektów bezpieczny i skuteczny przy użyciu definicji jednej klasy. Aby uzyskać więcej informacji dotyczących sposobu to zastąpienie odbywa się przez środowisko CLR, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Parametr typu zasady nazewnictwa  
  
-   **Czy** nazwy parametrów typu ogólnego z nazw opisowych, jeśli nazwa pojedyncze litery jest całkowicie self objaśniający i nazwę opisową nie może dodać wartość.  
  
     [!code-csharp[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]  
  
-   **Należy wziąć pod uwagę** przy użyciu T jako nazwę parametru typu dla typów z jednym parametrem typu pojedyncze litery.  
  
     [!code-csharp[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]  
  
-   **Czy** prefiksu nazwy parametrów opisowe typu z "T".  
  
     [!code-csharp[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]  
  
-   **Należy wziąć pod uwagę** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru. Na przykład parametr ograniczone do `ISession` może zostać wywołana `TSession`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
 [Różnice między szablonami C++ i typami ogólnymi C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
