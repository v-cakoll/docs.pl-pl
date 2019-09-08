---
title: Formułowanie projekcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: 0dfd5d951750de2ab918c51dd9f4f2deeb8a6318
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793817"
---
# <a name="formulate-projections"></a>Formułowanie projekcji
W poniższych przykładach pokazano, `select` jak instrukcje C# w `Select` instrukcji in i w Visual Basic mogą być łączone z innymi funkcjami w celu tworzenia zapytań dotyczących projekcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) do zwrócenia sekwencji nazw kontaktów dla `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić sekwencję nazw kontaktów i numerów `Customers`telefonów dla programu.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić sekwencję nazw i numerów telefonów dla pracowników. `Phone` `HomePhone` `Name`Pola i sąpołączone`LastName` w jedno pole (), a nazwa pola jest zmieniana na w `FirstName` wyniku sekwencji.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić sekwencję wszystkich `ProductID`i wartości obliczeniowej o nazwie. `HalfPrice` Ta wartość jest ustawiana na `UnitPrice` podzieloną przez 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Przykład  
 W `Select` poniższym przykładzie jest używana klauzula w Visual Basic (`select` klauzula in C#) i *Instrukcja warunkowa* zwracająca sekwencję nazwy produktu i dostępności produktu.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest używana klauzula `Select` Visual Basic (`select` klauzula in C#) i *znany typ* (nazwa) do zwrócenia sekwencji nazw pracowników.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Przykład  
 `Select` Poniższy przykład używa i `Where` w Visual Basic (`select` i `where` C#) do zwracania *filtrowanej sekwencji* nazw kontaktów dla klientów w Londynie.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `Select` klauzulę w Visual Basic`select` (klauzula C#in) i *Typy anonimowe* , aby zwrócić *podzbiór* danych dotyczących klientów.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa zagnieżdżonych zapytań, aby zwrócić następujące wyniki:  
  
- Sekwencja wszystkich zamówień i odpowiadających im `OrderID`elementów typu.  
  
- Podsekwencja elementów w kolejności, w której występuje rabat.  
  
- Ilość pieniędzy zapisana, jeśli koszt wysyłki nie jest uwzględniony.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
