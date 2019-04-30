---
title: Kwerenda dotycząca kolekcji obiektów (LINQ w C#)
description: Dowiedz się, jak wykonać zapytanie względem kolekcji za pomocą LINQ w C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659816"
---
# <a name="query-a-collection-of-objects"></a>Zapytanie dotyczące kolekcji obiektów

W tym przykładzie przedstawiono sposób wykonania prostego zapytania za pośrednictwem listy `Student` obiektów. Każdy `Student` obiekt zawiera niektóre podstawowe informacje o studenta i listę, która reprezentuje ocen studenta w czterech badań.  
  
Ta aplikacja służy jako umożliwiająca wiele innych przykładów w tej sekcji, które używały tych samych `students` źródła danych.  
  
## <a name="example"></a>Przykład

Następujące zapytanie zwraca studentów, którzy otrzymali wynik 90 lub nowszej na ich pierwsze egzamin.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
To zapytanie jest celowo proste umożliwiające eksperymentować. Na przykład, możesz spróbować więcej warunków w `where` klauzulę lub użyj `orderby` klauzulę, aby posortować wyniki.  
  
## <a name="see-also"></a>Zobacz także

- [Language Integrated Query (LINQ)](index.md)
- [Interpolacja ciągów](../language-reference/tokens/interpolated.md)
