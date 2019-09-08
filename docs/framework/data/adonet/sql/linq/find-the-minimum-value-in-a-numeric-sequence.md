---
title: Odnajdywanie wartości minimalnej w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: d8aee43f13ec92f649b4df20505ac56c336fe07a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793834"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a>Odnajdywanie wartości minimalnej w sekwencji numerycznej
<xref:System.Linq.Enumerable.Min%2A> Użyj operatora, aby zwrócić minimalną wartość z sekwencji wartości liczbowych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie znajduje się najniższa cena jednostkowa dowolnego produktu.  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `2.5000`.  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie najmniejszej ilości frachtu dla dowolnej kolejności.  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `0.0200`.  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest używane minimum, aby `Products` znaleźć wartość, która ma najniższą cenę jednostkową w każdej kategorii. Dane wyjściowe są uporządkowane według kategorii.  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 W przypadku uruchomienia poprzedniego zapytania względem przykładowej bazy danych Northwind wyniki będą wyglądać następująco:  
  
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

- [Zapytania zagregowane](aggregate-queries.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
