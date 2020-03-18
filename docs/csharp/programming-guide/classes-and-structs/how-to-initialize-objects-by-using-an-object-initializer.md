---
title: Jak zainicjować obiekty za pomocą inicjatora obiektów - Przewodnik programowania C#
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705590"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Jak zainicjować obiekty za pomocą inicjatora obiektów (Przewodnik programowania C#)

Można użyć inicjatorów obiektów do inicjowania obiektów typu w sposób deklaratywny bez jawnego wywoływania konstruktora dla typu.  
  
W poniższych przykładach przedstawiono sposób używania inicjatorów obiektów z nazwanymi obiektami. Kompilator przetwarza inicjatory obiektów, najpierw uzyskując dostęp do domyślnego konstruktora wystąpienia, a następnie przetwarzając inicjowania elementu członkowskiego. W związku z tym jeśli konstruktor bezparametrów jest zadeklarowany, jak `private` w klasie, inicjatory obiektów, które wymagają dostępu publicznego zakończy się niepowodzeniem.
  
Należy użyć inicjatora obiektów, jeśli definiujesz typ anonimowy. Aby uzyskać więcej informacji, zobacz [Jak zwrócić podzestawy właściwości elementu w kwerendzie](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Przykład  

W poniższym przykładzie pokazano, `StudentName` jak zainicjować nowy typ przy użyciu inicjatorów obiektów. W tym przykładzie ustawia `StudentName` właściwości w typie:
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Inicjatory obiektów mogą służyć do ustawiania indeksatorów w obiekcie. W poniższym `BaseballTeam` przykładzie definiuje klasę, która używa indeksatora, aby uzyskać i ustawić graczy na różnych pozycjach. Iinitor może przypisać graczy, na podstawie skrótu pozycji, lub liczby używanej dla każdej pozycji baseball karty wyników:

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Inicjatory obiektów i kolekcji](object-and-collection-initializers.md)
