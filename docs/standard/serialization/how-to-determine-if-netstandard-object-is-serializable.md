---
title: Jak ustalić, czy obiekt standardowy .NET jest możliwy do serializacji
description: Pokazuje, jak ustalić, czy typ .NET Standard może być serializowany w czasie wykonywania.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018765"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Jak ustalić, czy obiekt standardowy .NET jest możliwy do serializacji

.NET Standard to specyfikacja, która definiuje typy i elementy członkowskie, które musi znajdować się na określonej implementacji platformy .NET, które są zgodne z wersji standard. Jednak .NET Standard nie definiuje czy typ jest możliwy do serializacji. Typy zdefiniowane w standardowej bibliotece platformy .NET nie są oznaczone <xref:System.SerializableAttribute> atrybutu. Zamiast tego określonej implementacji platformy .NET, takich jak .NET Framework i .NET Core mogą swobodnie ustalać, czy określony typ jest możliwy do serializacji. 

Tworzyli biblioteki .NET Standard przeznaczonego, biblioteki mogą być używane przez wszystkie implementacji .NET, która obsługuje .NET Standard. Oznacza to, że możesz nie wiedzieć z wyprzedzeniem czy określonego typu jest możliwy do serializacji; należy tylko określić, czy jest możliwy do serializacji w czasie wykonywania.

Można określić, czy obiekt jest możliwy do serializacji w czasie wykonywania, poprzez pobranie wartości <xref:System.Type.IsSerializable> właściwość <xref:System.Type> obiektu, który reprezentuje typ tego obiektu. W poniższym przykładzie przedstawiono jedna implementacja. Definiuje on `IsSerializable(Object)` metodę rozszerzenia, która wskazuje, czy którekolwiek <xref:System.Object> wystąpienia może być serializowany.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Dowolny obiekt można następnie przekazać do metody w celu określenia, czy może być serializacji i deserializacji bieżącej implementacji .NET, co ilustruje poniższy przykład:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
