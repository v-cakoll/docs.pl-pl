---
title: Ogólne parametry typu — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: 8412980d35989c445d2e0a44c0b9f35e6087bb8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712185"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Ogólne parametry typu (Przewodnik programowania C#)

W definicji typu ogólnego lub metody parametr typu jest symbolem zastępczym dla określonego typu, który klient określa podczas tworzenia wystąpienia typu ogólnego. Klasy ogólnej, `GenericList<T>` takich jak wymienione w [wprowadzenie do leków ogólnych](./index.md), nie można używać jako- jest, ponieważ nie jest to naprawdę typ; jest bardziej jak plan dla typu. Aby `GenericList<T>`użyć , kod klienta musi zadeklarować i utworzyć wystąpienie skonstruowanego typu, określając argument typu wewnątrz nawiasów kątowych. Argument typu dla tej określonej klasy może być dowolny typ rozpoznawany przez kompilator. Można utworzyć dowolną liczbę skonstruowanych wystąpień typu, z których każdy przy użyciu innego typu argumentu, w następujący sposób:  
  
[!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
W każdym z tych `GenericList<T>`wystąpień `T` , każde wystąpienie w klasie jest zastępowane w czasie wykonywania argumentem typu. Za pomocą tej podstawienia utworzyliśmy trzy oddzielne obiekty bezpieczne dla typów i wydajne przy użyciu definicji jednej klasy. Aby uzyskać więcej informacji na temat sposobu wykonywania tego podstawienia przez clr, zobacz [Generyków w czasie wykonywania](./generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Wskazówki dotyczące nazewnictwa parametrów typu  
  
- **Czy** nazwać ogólne parametry typu z nazwami opisowymi, chyba że nazwa pojedynczej litery jest całkowicie oczywiste i nazwa opisowa nie doda wartości.  
  
   [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
- **Należy rozważyć** użycie T jako nazwy parametru typu dla typów z jednym parametrem typu litery.  
  
   [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
- **Wykonaj** nazwy parametrów typu opisowego prefiksu z "T".  
  
   [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
- **Należy wziąć pod uwagę** wskazując ograniczenia umieszczone na parametr typu w nazwie parametru. Na przykład parametr ograniczony do `ISession` może `TSession`być wywoływana .

Reguła analizy kodu [CA1715](/visualstudio/code-quality/ca1715) może służyć do zapewnienia, że parametry typu są odpowiednio nazwane.
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania języka C#](../index.md)
- [Typy ogólne](./index.md)
- [Różnice między szablonami C++ i typami ogólnymi C#](./differences-between-cpp-templates-and-csharp-generics.md)
