---
title: Inicjowanie obiektów za pomocą inicjatora obiektów — C# Przewodnik programowania
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705590"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Inicjowanie obiektów za pomocą inicjatora obiektów (C# Przewodnik programowania)

Inicjatorów obiektów można użyć do zainicjowania obiektów typu w sposób deklaratywny bez jawnego wywołania konstruktora dla tego typu.  
  
W poniższych przykładach pokazano, jak używać inicjatorów obiektów z nazwanymi obiektami. Kompilator przetwarza Inicjatory obiektów, najpierw uzyskując dostęp do domyślnego konstruktora wystąpień, a następnie przetwarza inicjalizacje elementu członkowskiego. W związku z tym, jeśli Konstruktor bez parametrów jest zadeklarowany jako `private` w klasie, Inicjatory obiektów, które wymagają dostępu publicznego, zakończą się niepowodzeniem.
  
Jeśli jest definiowany typ anonimowy, należy użyć inicjatora obiektów. Aby uzyskać więcej informacji, zobacz [jak zwrócić podzbiory właściwości elementu w zapytaniu](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Przykład  

Poniższy przykład pokazuje, jak zainicjować nowy typ `StudentName` przy użyciu inicjatorów obiektów. Ten przykład ustawia właściwości w `StudentName` typie:
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Inicjatory obiektów mogą służyć do ustawiania indeksatorów w obiekcie. W poniższym przykładzie zdefiniowano klasę `BaseballTeam`, która używa indeksatora do pobierania i ustawiania graczy w różnych miejscach. Inicjator może przypisywać graczy na podstawie skrótu do pozycji lub liczby użytej dla każdej pozycji siatkówki karty wyników:

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Inicjatory obiektów i kolekcji](object-and-collection-initializers.md)
