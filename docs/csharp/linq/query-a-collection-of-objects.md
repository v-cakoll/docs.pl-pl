---
title: Kwerenda kolekcji obiektów (LINQ w języku C#)
description: Dowiedz się, jak kolekcje zapytań przy użyciu LINQ w języku C#.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659816"
---
# <a name="query-a-collection-of-objects"></a>Zapytanie dotyczące kolekcji obiektów

W tym przykładzie pokazano, jak wykonać `Student` prostą kwerendę za pomocą listy obiektów. Każdy `Student` obiekt zawiera podstawowe informacje o uczniu i listę, która reprezentuje wyniki ucznia na czterech egzaminach.  
  
Ta aplikacja służy jako ramy dla wielu innych przykładów `students` w tej sekcji, które używają tego samego źródła danych.  
  
## <a name="example"></a>Przykład

Następujące zapytanie zwraca uczniom, którzy otrzymali wynik 90 lub więcej na pierwszym egzaminie.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
Ta kwerenda jest celowo proste, aby umożliwić eksperymentowanie. Na przykład można spróbować więcej `where` warunków w klauzuli lub użyć `orderby` klauzuli do sortowania wyników.  
  
## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
- [Interpolacja ciągów](../language-reference/tokens/interpolated.md)
