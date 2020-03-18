---
title: Zamów wyniki klauzuli sprzężenia (LINQ w języku C#)
description: Dowiedz się, jak uporządkować wyniki linq join klauzuli w języku C#.
ms.date: 12/01/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f60000b83bf378dd8740b7255d421dd4335614c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659868"
---
# <a name="order-the-results-of-a-join-clause"></a>Kolejność wyników klauzuli join

W tym przykładzie pokazano, jak uporządkować wyniki operacji sprzężenia. Należy zauważyć, że kolejność jest wykonywana po sprzężeniu. Mimo że można `orderby` użyć klauzuli z co najmniej jedną sekwencją źródłową przed sprzężeniem, zazwyczaj nie zaleca się jej. Niektórzy dostawcy LINQ może nie zachować, że kolejność po sprzężeniu.

## <a name="example"></a>Przykład

Ta kwerenda tworzy sprzężenie grupy, a następnie sortuje grupy na podstawie elementu kategorii, który nadal znajduje się w zakresie. Wewnątrz inicjatora typu anonimowego kwerenda podrzędna porządkuje wszystkie pasujące elementy z sekwencji produktów.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
- [Klauzula orderby](../language-reference/keywords/orderby-clause.md)
- [klauzula sprzężenia](../language-reference/keywords/join-clause.md)
