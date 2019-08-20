---
title: C# informacje o interfejsie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 058d6b96e96a3237ebac2ca079807fd154715d68
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608650"
---
# <a name="interface-c-reference"></a>interface (odwołanie w C#)

Interfejs zawiera tylko sygnatury [metod](../../programming-guide/classes-and-structs/methods.md), [Właściwości](../../programming-guide/classes-and-structs/properties.md), [zdarzeń](../../programming-guide/events/index.md) i indeksatorów [](../../programming-guide/indexers/index.md). Klasa lub struktura implementująca interfejs musi implementować elementy członkowskie interfejsu, które są określone w definicji interfejsu. W poniższym przykładzie Klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` , która nie ma parametrów i zwraca `void`.

Aby uzyskać więcej informacji i przykładów, zobacz [interfejsy](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Interfejs może być elementem członkowskim przestrzeni nazw lub klasy i może zawierać podpisy następujących elementów członkowskich:

- [Metody](../../programming-guide/classes-and-structs/methods.md)

- [Właściwości](../../programming-guide/classes-and-structs/using-properties.md)

- [Indeksatory](../../programming-guide/indexers/using-indexers.md)

- [Zdarzenia](event.md)

Interfejs może dziedziczyć z jednego lub kilku interfejsów podstawowych.

Gdy lista typów podstawowych zawiera klasę bazową i interfejsy, Klasa bazowa musi znajdować się na liście.

Klasa implementująca interfejs może jawnie implementować elementy członkowskie tego interfejsu. Nie można uzyskać dostępu do jawnie zaimplementowanego elementu członkowskiego za pomocą wystąpienia klasy, ale tylko za pomocą wystąpienia interfejsu.

Aby uzyskać szczegółowe informacje i przykłady kodu w przypadku jawnej implementacji interfejsu, zobacz [jawną implementację interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje implementację interfejsu. W tym przykładzie interfejs zawiera deklarację właściwości, a Klasa zawiera implementację. Każde wystąpienie klasy implementującej `IPoint` zawiera właściwości `x` całkowite i `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy odwołań](reference-types.md)
- [Interfejsy](../../programming-guide/interfaces/index.md)
- [Używanie właściwości](../../programming-guide/classes-and-structs/using-properties.md)
- [Używanie indeksatorów](../../programming-guide/indexers/using-indexers.md)
- [class](class.md)
- [struct](struct.md)
- [Interfejsy](../../programming-guide/interfaces/index.md)
