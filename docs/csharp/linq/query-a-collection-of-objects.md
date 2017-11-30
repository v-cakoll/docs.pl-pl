---
title: "Kwerenda dotycząca kolekcji obiektów"
description: "Jak zapytanie względem kolekcji."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Ciągi interpolowane](../language-reference/keywords/interpolated-strings.md)
