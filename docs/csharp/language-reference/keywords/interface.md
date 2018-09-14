---
title: interface (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619204"
---
# <a name="interface-c-reference"></a>interface (odwołanie w C#)

Interfejs zawiera tylko sygnatury [metody](../../programming-guide/classes-and-structs/methods.md), [właściwości](../../programming-guide/classes-and-structs/properties.md), [zdarzenia](../../programming-guide/events/index.md) lub [indeksatory](../../programming-guide/indexers/index.md). Klasa lub struktura implementująca interfejs musi implementować składowych interfejsu, które są określone w definicji interfejsu. W poniższym przykładzie klasa `ImplementationClass` musi implementować metodę o nazwie `SampleMethod` , nie ma parametrów i zwraca `void`.

Aby uzyskać więcej informacji i przykładów, zobacz [interfejsów](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Interfejs może być elementem członkowskim klasy lub przestrzeni nazw i może zawierać podpisy następujące elementy członkowskie:

- [Metody](../../programming-guide/classes-and-structs/methods.md)

- [Właściwości](../../programming-guide/classes-and-structs/using-properties.md)

- [Indeksatory](../../programming-guide/indexers/using-indexers.md)

- [Zdarzenia](event.md)

Interfejs może dziedziczyć z jednego lub więcej podstawowych interfejsów.

Gdy listy Typ podstawowy zawiera klasę bazową i interfejsy, pierwszy na liście musi występować klasa bazowa.

Klasa, która implementuje interfejs może jawne Implementowanie elementów interfejsu. Jawnie implementowane elementu członkowskiego nie są dostępne za pośrednictwem wystąpienia klasy, ale tylko za pośrednictwem wystąpienia interfejsu.

Aby uzyskać więcej informacji i przykładów kodu w jawnej implementacji interfejsu, zobacz [jawnej implementacji interfejsu](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano implementację interfejsu. W tym przykładzie interfejs zawiera deklarację właściwości, a klasa zawiera implementację. Wszystkie wystąpienia klasy, która implementuje `IPoint` ma właściwości Liczba całkowita `x` i `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Słowa kluczowe języka C#](index.md)  
- [Typy odwołań](reference-types.md)  
- [Interfejsy](../../programming-guide/interfaces/index.md)  
- [Używanie właściwości](../../programming-guide/classes-and-structs/using-properties.md)  
- [Używanie indeksatorów](../../programming-guide/indexers/using-indexers.md)  
- [class](class.md)  
- [struct](struct.md)  
- [Interfejsy](../../programming-guide/interfaces/index.md)
