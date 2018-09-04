---
title: Kolejność wyników klauzuli join (LINQ w C#)
description: Dowiedz się, jak kolejność wyników klauzuli join LINQ w C#.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: 13cd6cb202cf67def17310db6d98e368ce837646
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516989"
---
# <a name="order-the-results-of-a-join-clause"></a>Kolejność wyników klauzuli join

W tym przykładzie przedstawiono sposób uporządkowania wyników operacji tworzenia sprzężenia. Należy pamiętać, że kolejność jest wykonywana po sprzężenia. Chociaż można używać `orderby` klauzuli z co najmniej źródła sekwencji przed sprzężenia, ogólnie nie zalecamy tego. Niektórzy dostawcy LINQ może zachować kolejności po sprzężenia.

## <a name="example"></a>Przykład

To zapytanie tworzy sprzężenie grupy, a następnie sortuje grup oparty na element kategorii, który jest nadal w zakresie. Wewnątrz inicjatora typu anonimowego podzapytaniu zamówień zgodnych elementów z sekwencji produktów.

[!code-csharp[csProgGuideLINQ#81](~/samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]

## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)  
- [orderby, klauzula](../language-reference/keywords/orderby-clause.md)  
- [join, klauzula](../language-reference/keywords/join-clause.md)  