---
title: 'Instrukcje: Inicjowanie obiektów za pomocą obiektu inicjatora - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 494b7625ff8e90b1b81fd32de031ff60d5c6d029
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973645"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Instrukcje: Inicjowanie obiektów za pomocą inicjatora obiektów (C# Programming Guide)

Inicjatory obiektów można użyć do zainicjowania obiekty typu w sposób deklaratywne, bez jawnego wywołania konstruktora dla typu.  
  
Poniższe przykłady pokazują, jak używać inicjatory obiektów z nazwane obiekty. Procesy kompilatora obiekt inicjatory pierwszego uzyskiwania dostępu do domyślnego konstruktora wystąpienia, a następnie przetwarzania operacji inicjowania elementu członkowskiego. W związku z tym jeśli konstruktora bez parametrów jest zadeklarowany jako `private` w klasie inicjatorów obiektów, które wymagają dostępu publicznego zakończy się niepowodzeniem.
  
Jeśli definiujesz typ anonimowy, należy użyć inicjatora obiektu. Aby uzyskać więcej informacji, zobacz [jak: Zwracanie podzbiorów właściwości elementu w zapytaniu](how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Przykład  

Poniższy przykład pokazuje, jak zainicjować nowy `StudentName` typu przy użyciu inicjatorów obiektów. W tym przykładzie ustawia właściwości w `StudentName` typu:
  
[!code-csharp-interactive[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

Inicjatory obiektów może służyć do ustawiania indeksatorów w obiekcie. W poniższym przykładzie zdefiniowano `BaseballTeam` klasę, która używa indeksator do pobierania i ustawiania graczy w różnych miejscach. Inicjator można przypisać odtwarzaczy, w oparciu o skrót dla pozycji, lub numer używany dla każdej karty wyników mecz pozycji:

[!code-csharp-interactive[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Inicjatory obiektów i kolekcji](object-and-collection-initializers.md)
