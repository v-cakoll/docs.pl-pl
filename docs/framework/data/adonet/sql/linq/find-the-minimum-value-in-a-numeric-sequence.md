---
title: Znajdowanie wartości minimalnej w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: f92558798267760eb6cfd1bfc6365451cdcc1c62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529999"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a>Znajdowanie wartości minimalnej w sekwencji numerycznej
Użyj <xref:System.Linq.Enumerable.Min%2A> operator, aby zwrócić wartość minimalna z sekwencji wartości liczbowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie najniższą cenę jednostkową jakiegokolwiek produktu.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `2.5000`.  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie najmniejszą Fracht dowolnej kolejności.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `0.0200`.  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto Min, aby znaleźć `Products` mają najniższą cenę jednostkową w każdej kategorii. Dane wyjściowe są uporządkowane według kategorii.  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 Jeśli uruchamiasz poprzednie zapytanie względem przykładowej bazy danych Northwind, wyniki będą wyglądać w następujący sposób:  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a>Zobacz także
- [Zapytania zagregowane](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
