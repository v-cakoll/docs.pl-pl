---
title: Kwerenda dotycząca kolekcji obiektów (LINQ w C#)
description: Dowiedz się, jak wykonać zapytanie względem kolekcji za pomocą LINQ w C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 87c7bbe789c165a6e189231df1979fc264a34dce
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2018
ms.locfileid: "37403924"
---
# <a name="query-a-collection-of-objects"></a>Kwerenda dotycząca kolekcji obiektów

W tym przykładzie przedstawiono sposób wykonania prostego zapytania za pośrednictwem listy `Student` obiektów. Każdy `Student` obiekt zawiera niektóre podstawowe informacje o studenta i listę, która reprezentuje ocen studenta w czterech badań.  
  
Ta aplikacja służy jako umożliwiająca wiele innych przykładów w tej sekcji, które używały tych samych `students` źródła danych.  
  
## <a name="example"></a>Przykład

Następujące zapytanie zwraca studentów, którzy otrzymali wynik 90 lub nowszej na ich pierwsze egzamin.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
To zapytanie jest celowo proste umożliwiające eksperymentować. Na przykład, możesz spróbować więcej warunków w `where` klauzulę lub użyj `orderby` klauzulę, aby posortować wyniki.  
  
## <a name="see-also"></a>Zobacz także

[Language Integrated Query (LINQ)](index.md)  
[Interpolacja ciągów](../language-reference/tokens/interpolated.md)