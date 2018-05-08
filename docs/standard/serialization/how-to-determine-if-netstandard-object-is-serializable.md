---
title: 'Porady: Określa, czy obiekt .NET Standard jest możliwy do serializacji'
description: Pokazuje sposób określania, czy w czasie wykonywania można zserializować typu .NET Standard.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 247eed2e7091930c6bcfaa524296b45350dd6510
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Porady: Określa, czy obiekt .NET Standard jest możliwy do serializacji

.NET Standard jest specyfikacją definiujący typy i elementy członkowskie, które musi znajdować się na określonych implementacje .NET, które są zgodne z danej wersji standard. Jednak .NET Standard nie definiuje czy typ jest możliwy do serializacji. Typów zdefiniowanych w standardowej bibliotece programu .NET nie jest oznaczony atrybutem <xref:System.SerializableAttribute> atrybutu. Zamiast tego określonego implementacji .NET, takich jak .NET Framework i .NET Core mogą ustalić, czy określony typ jest możliwy do serializacji. 

Jeśli został opracowany biblioteki którego element docelowy .NET Standard, biblioteki mogą być używane przez wszystkie implementacja .NET obsługuje .NET Standard. Oznacza to, że nie znasz z wyprzedzeniem czy konkretny typ jest możliwy do serializacji; można tylko określić, czy jest możliwy do serializacji w czasie wykonywania.

Można określić, czy obiekt jest możliwy do serializacji w czasie wykonywania, pobierając zaletą <xref:System.Type.IsSerializable> właściwość <xref:System.Type> obiekt, który reprezentuje typ tego obiektu. W poniższym przykładzie przedstawiono jeden implementacji. Definiuje `IsSerializable(Object)` — metoda rozszerzenia, która wskazuje, czy którekolwiek <xref:System.Object> wystąpienie może być Zserializowany.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Dowolny obiekt można następnie przekazać do metody w celu określenia, czy może być serializacji i deserializacji bieżąca implementacja .NET, jak przedstawiono na poniższym przykładzie:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a>Zobacz także

[Serializacja binarna](binary-serialization.md)   
<xref:System.SerializableAttribute?displayProperty=nameWithType>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
