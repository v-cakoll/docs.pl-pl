---
title: Formułowanie projekcji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: e1f7a7da1ab2ce0ad7d7908ecd1f896d229b8e1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037911"
---
# <a name="formulate-projections"></a>Formułowanie projekcji
W poniższych przykładach pokazano sposób, w jaki `select` instrukcji w C# i `Select` instrukcji w języku Visual Basic można łączyć z innymi funkcjami do formularza projekcje zapytania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) do zwrócenia sekwencji skontaktuj się z nazwy `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* do zwrócenia sekwencji skontaktuj się z nazwy i numery telefonu `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* do zwrócenia sekwencji nazwy i numery telefonów dla pracowników. `FirstName` i `LastName` pola są połączone w jedno pole (`Name`), a `HomePhone` pola została zmieniona na `Phone` w wynikowej sekwencji.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* celu zwrócenia sekwencji wszystkich `ProductID`s i obliczonej wartości o nazwie `HalfPrice`. Ta wartość jest równa `UnitPrice` podzielonej przez 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *instrukcji warunkowej* celu zwrócenia sekwencji nazwę produktu i dostępność produktu.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto języka Visual Basic `Select` — klauzula (`select` w klauzuli C#) i *znany typ* (nazwa) w celu zwrócenia sekwencji nazw pracowników.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` i `Where` w języku Visual Basic (`select` i `where` w C#) do zwrócenia *filtrowane sekwencji* nazw kontaktu dla klientów w Londynie.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) i *typy anonimowe* do zwrócenia *ukształtowane podzbioru* danych dotyczących klientów.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto zapytań zagnieżdżonej, aby zostały zwrócone następujące wyniki:  
  
- Sekwencja wszystkich zamówień i odpowiadające im `OrderID`s.  
  
- Podsekwencji elementy w kolejności, dla którego jest rabat.  
  
- Ilość pieniądze zapisane, jeżeli nie dołączono kosztu wysyłki.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
