---
title: Tworzenie grupy zagnieżdżonej (LINQ w języku C#)
description: Dowiedz się, jak utworzyć grupę zagnieżdżoną w wyrażeniu kwerendy LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 7d056c9e215ccc7ca24d621b64e2328bed79f22e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688621"
---
# <a name="create-a-nested-group"></a>Tworzenie grupy zagnieżdżonej

W poniższym przykładzie pokazano, jak tworzyć grupy zagnieżdżone w wyrażeniu kwerendy LINQ. Każda grupa, która jest tworzona zgodnie z rokiem studenckim lub poziomem oceny, jest następnie podzielona na grupy na podstawie imion osób.

## <a name="example"></a>Przykład

> [!NOTE]
> W tym przykładzie znajdują się odwołania do obiektów zdefiniowanych w przykładowym kodzie w [query kolekcji obiektów](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#24](~/samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]

Należy zauważyć, `foreach` że trzy zagnieżdżone pętle są wymagane do itetensji nad elementami wewnętrznymi grupy zagnieżdżonej.

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
