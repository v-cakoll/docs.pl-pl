---
title: Tworzenie grup zagnieżdżonych (LINQ w C#)
description: Dowiedz się, jak tworzenie grup zagnieżdżonych w wyrażeniu zapytania LINQ w C#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857674"
---
# <a name="create-a-nested-group"></a>Tworzenie grup zagnieżdżonych

Poniższy przykład pokazuje, jak tworzyć grupy zagnieżdżone w wyrażeniu zapytania LINQ. Każda grupa, utworzony zgodnie z poziomem roku lub klasy korporacyjnej dla uczniów następnie jest podzielona na grupy na podstawie nazw poszczególnych osób.

## <a name="example"></a>Przykład

> [!NOTE]
> Ten przykład zawiera odwołania do obiektów, które są zdefiniowane w przykładowym kodzie w [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

Należy zauważyć, że trzy zagnieżdżone `foreach` pętle są wymagane do wykonywania iteracji wewnętrzne elementy zagnieżdżone grupy.

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)
