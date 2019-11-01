---
title: Parametry typu ogólnego — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 992b71fa2afa6b511d09c69ade26e3b5bc13acd2
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195476"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parametry typu ogólnego (C# Przewodnik programowania)

W przypadku typu ogólnego lub definicji metody parametr typu jest symbolem zastępczym określonego typu, który klient określa podczas tworzenia wystąpienia typu ogólnego. Klasa generyczna, taka jak `GenericList<T>` wymieniona w temacie [wprowadzenie do typów ogólnych](./index.md), nie może być używana jako-jest, ponieważ nie jest w rzeczywistości typem. jest to bardziej podobne do planu dla typu. Aby użyć `GenericList<T>`, kod klienta musi deklarować i utworzyć wystąpienie złożonego typu przez określenie argumentu typu wewnątrz nawiasów kątowych. Argument typu dla tej konkretnej klasy może być dowolnym typem rozpoznawanym przez kompilator. Można utworzyć dowolną liczbę wystąpień typu złożonego, każdy z nich przy użyciu innego argumentu typu, w następujący sposób:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
W każdym z tych wystąpień `GenericList<T>`każde wystąpienie `T` w klasie jest zastępowane w czasie wykonywania z argumentem typu. Zgodnie z tym podstawianiem zostały utworzone trzy osobne, bezpieczne obiekty typu za pomocą jednej definicji klasy. Aby uzyskać więcej informacji o tym, jak to podstawienie jest wykonywane przez środowisko CLR, zobacz [typy ogólne w czasie wykonywania](./generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Wskazówki dotyczące nazewnictwa parametrów typu  
  
- **Należy** nazywać parametry typu ogólnego z nazwami opisowymi, chyba że nazwa pojedynczej litery nie jest całkowicie oczywista, a nazwa opisowa nie będzie dodawać wartości.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Rozważ** użycie T jako nazwy parametru typu dla typów z jednym pojedynczym parametrem typu.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Wykonaj** prefiks nazwy parametrów typu opisowego z "T".  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Rozważ** wskazanie ograniczeń umieszczanych na parametrze typu w nazwie parametru. Na przykład parametr ograniczony do `ISession` może być wywołany `TSession`.

Reguły analizy kodu [CA1715](/visualstudio/code-quality/ca1715) można użyć, aby upewnić się, że parametry typu są odpowiednio nazwane.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Typy ogólne](./index.md)
- [Różnice między szablonami C++ i typami ogólnymi C#](./differences-between-cpp-templates-and-csharp-generics.md)
