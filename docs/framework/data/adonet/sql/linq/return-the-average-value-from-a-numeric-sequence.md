---
title: Zwracanie średniej wartości z sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: eea1439337b29fee51c422238425491fc2345211
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095090"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a>Zwracanie średniej wartości z sekwencji numerycznej
<xref:System.Linq.Enumerable.Average%2A> Operator oblicza średnią sekwencję wartości liczbowych.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tłumaczenia `Average` liczby całkowitej wartości jest obliczany jako liczba całkowita, nie jako wartość o podwójnej precyzji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca średnią `Freight` wartości w `Orders` tabeli.  
  
 Wyniki z przykładowej bazy danych Northwind będą `78.2442`.  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca średnią cenę jednostkową wszystkich `Products` w `Products` tabeli.  
  
 Wyniki z przykładowej bazy danych Northwind będą `28.8663`.  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Average` operatora, aby znaleźć te `Products` których cena jednostkowa jest wyższa niż średnia cena jednostkowa kategorii, należy ona do. Przykład następnie wyświetla wyniki w grupach.  
  
 Należy pamiętać, że w tym przykładzie wymaga użycia `var` — słowo kluczowe w C#, ponieważ zwracany typ jest anonimowy.  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki powinien przypominać poniższe:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania zagregowane](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
