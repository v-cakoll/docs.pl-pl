---
title: Zwracanie średniej wartości z sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 8d6f5f76787c1110e91b245a3dd2425450b4db7e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781393"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a>Zwracanie średniej wartości z sekwencji numerycznej
<xref:System.Linq.Enumerable.Average%2A> Operator oblicza średnią sekwencji wartości liczbowych.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Tłumaczeniewartościcałkowitychjestobliczanejakoliczbacałkowita`Average` , nie jako Double.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca średnią `Freight` wartości `Orders` w tabeli.  
  
 Wyniki z przykładowej bazy danych Northwind byłyby `78.2442`.  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca średnią cenę jednostkową wszystkich `Products` `Products` w tabeli.  
  
 Wyniki z przykładowej bazy danych Northwind byłyby `28.8663`.  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `Average` aby znaleźć te `Products` , których cena jednostkowa jest wyższa niż średnia cena jednostkowa kategorii, do której należy. Przykład następnie wyświetla wyniki w grupach.  
  
 Należy zauważyć, że ten przykład wymaga użycia `var` słowa kluczowego w C#, ponieważ zwracany typ jest anonimowy.  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind wyniki powinny wyglądać następująco:  
  
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

- [Zapytania zagregowane](aggregate-queries.md)
