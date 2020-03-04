---
title: Jak ustalić, czy obiekt .NET Standard jest możliwy do serializacji
description: Pokazuje, jak ustalić, czy typ .NET Standard może być serializowany w czasie wykonywania.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: 4037dee36aeb619eb2757016904fd877158e57cf
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159900"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Jak ustalić, czy obiekt .NET Standard jest możliwy do serializacji

.NET Standard to specyfikacja, która definiuje typy i elementy członkowskie, które muszą być obecne w określonych implementacjach platformy .NET, które są zgodne z tą wersją Standard. Jednak .NET Standard nie definiuje, czy typ jest możliwy do serializacji. Typy zdefiniowane w bibliotece .NET Standard nie są oznaczone atrybutem <xref:System.SerializableAttribute>. Zamiast tego konkretne implementacje platformy .NET, takie jak .NET Framework i .NET Core, są bezpłatne, aby określić, czy dany typ jest możliwy do serializacji.

Jeśli opracowano bibliotekę, która jest przeznaczona dla .NET Standard, biblioteka może być używana przez dowolną implementację platformy .NET, która obsługuje .NET Standard. Oznacza to, że nie można wcześniej sprawdzić, czy dany typ jest możliwy do serializacji; można określić tylko, czy ma on być możliwy do serializacji w czasie wykonywania.

Można określić, czy obiekt jest możliwy do serializacji w czasie wykonywania przez pobranie wartości właściwości <xref:System.Type.IsSerializable> obiektu <xref:System.Type>, który reprezentuje typ tego obiektu. Poniższy przykład zawiera jedną implementację. Definiuje metodę rozszerzenia `IsSerializable(Object)`, która wskazuje, czy dowolne wystąpienie <xref:System.Object> może być serializowane.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Następnie można przekazać dowolny obiekt do metody, aby określić, czy można serializować i zdeserializować w bieżącej implementacji platformy .NET, jak pokazano na poniższym przykładzie:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Zobacz też

- [Serializacja binarna](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
