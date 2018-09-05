---
title: Tworzenie grup zagnieżdżonych (LINQ w C#)
description: Dowiedz się, jak tworzenie grup zagnieżdżonych w wyrażeniu zapytania LINQ w C#.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 82b07c303215200fa974ce614a2d5a77882dcf4c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509971"
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
