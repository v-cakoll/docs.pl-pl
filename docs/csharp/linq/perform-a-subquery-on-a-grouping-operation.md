---
title: Wykonywanie podkwerendy w operacji grupowania (LINQ w języku C#)
description: Jak wykonać podkwerendę w operacji grupowania przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: fd26f87ad7d5b4892f086bf8c7a34cf19a7f9e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173370"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Wykonywanie podzapytania w operacji grupowania

W tym artykule przedstawiono dwa różne sposoby tworzenia kwerendy, która porządkuje dane źródłowe w grupy, a następnie wykonuje podkwerendę nad każdą grupą indywidualnie. Podstawową techniką w każdym przykładzie jest grupowanie `newGroup`elementów źródłowych przy użyciu `newGroup` *kontynuacji* o nazwie , a następnie generowanie nowej podkwerendy przeciwko . To podkwerenda jest uruchamiana dla każdej nowej grupy utworzonej przez kwerendę zewnętrzną. Należy zauważyć, że w tym konkretnym przykładzie ostateczne dane wyjściowe nie jest grupa, ale płaska sekwencja typów anonimowych.  
  
Aby uzyskać więcej informacji na temat grupowania, zobacz [klauzulę grupy](../language-reference/keywords/group-clause.md).  
  
Aby uzyskać więcej informacji na temat kontynuacji, zobacz [w](../language-reference/keywords/into.md). W poniższym przykładzie używa struktury danych w pamięci jako źródła danych, ale te same zasady mają zastosowanie do dowolnego rodzaju źródła danych LINQ.  
  
## <a name="example"></a>Przykład

> [!NOTE]
> W tym przykładzie znajdują się odwołania do obiektów zdefiniowanych w przykładowym kodzie w [query kolekcji obiektów](query-a-collection-of-objects.md).

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]

Kwerenda w powyższym fragmencie kodu może być również zapisywana przy użyciu składni metody. Poniższy fragment kodu zawiera semantycznie równoważną kwerendę napisaną przy użyciu składni metody.

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
