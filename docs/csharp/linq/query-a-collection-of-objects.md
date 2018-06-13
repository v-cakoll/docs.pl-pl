---
title: Kwerenda dotycząca kolekcji obiektów
description: Jak zapytanie względem kolekcji.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: c690da2ae59d2a9b34a5bd403bc54797c4e95fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282395"
---
# <a name="query-a-collection-of-objects"></a>Kwerenda dotycząca kolekcji obiektów
W tym przykładzie przedstawiono sposób wykonania prostego zapytania listy `Student` obiektów. Każdy `Student` obiektu zawiera niektóre podstawowe informacje o student i listę, która reprezentuje studentów w czterech badania.  
  
 Ta aplikacja służy jako platforma wiele innych przykładów w tej sekcji, które korzystają z jednego `students` źródła danych.  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie zwraca studentów, którzy otrzymali wynikiem 90 lub większa na ich pierwsze egzaminu.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 To zapytanie jest celowo proste do eksperymentu. Na przykład spróbujesz więcej warunków w `where` klauzulę lub użyj `orderby` klauzuli sortowania wyników.  
  

## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)  
 [Interpolacja ciągów](../language-reference/tokens/interpolated.md)
