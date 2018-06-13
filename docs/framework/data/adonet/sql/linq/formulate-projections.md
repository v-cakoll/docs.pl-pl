---
title: Sformułować projekcje
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 745742df-0eda-479b-83f8-29bd8a80db96
ms.openlocfilehash: f554007bd8c9e69f6a8dc475c122d3fbdfc43a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364951"
---
# <a name="formulate-projections"></a>Sformułować projekcje
W poniższych przykładach pokazano sposób `select` instrukcji w języku C# i `Select` instrukcji w języku Visual Basic można łączyć z innymi funkcjami do formularza projekcje zapytania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) do zwrócenia sekwencji kontaktu nazw `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#57](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#57)]
 [!code-vb[DLinqQueryExamples#57](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#57)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* zwraca sekwencję nazwy kontaktów i numerów telefonu `Customers`.  
  
 [!code-csharp[DLinqQueryExamples#58](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#58)]
 [!code-vb[DLinqQueryExamples#58](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#58)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* zwraca sekwencję nazwy i numery telefonów dla pracowników. `FirstName` i `LastName` pola są łączone w jedno pole (`Name`) i `HomePhone` pole jest zmieniana na `Phone` w wynikowej sekwencji.  
  
 [!code-csharp[DLinqQueryExamples#59](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#59)]
 [!code-vb[DLinqQueryExamples#59](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#59)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* do zwrócenia sekwencji wszystkich `ProductID`s i obliczonej wartości o nazwie `HalfPrice`. Ta wartość jest równa `UnitPrice` podzielona przez 2.  
  
 [!code-csharp[DLinqQueryExamples#60](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#60)]
 [!code-vb[DLinqQueryExamples#60](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#60)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *instrukcji warunkowej* do zwrócenia sekwencji dostępności produktu i nazwa produktu.  
  
 [!code-csharp[DLinqQueryExamples#61](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#61)]
 [!code-vb[DLinqQueryExamples#61](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#61)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto języka Visual Basic `Select` klauzuli (`select` klauzuli w języku C#) i *znany typ* (nazwy), aby znaleźć sekwencję imiona i nazwiska pracowników.  
  
 [!code-csharp[DLinqQueryExamples#62](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#62)]
 [!code-vb[DLinqQueryExamples#62](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#62)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` i `Where` w języku Visual Basic (`select` i `where` w języku C#) do zwrócenia *filtrowane sekwencji* nazw kontaktu dla klientów w Londynie.  
  
 [!code-csharp[DLinqQueryExamples#63](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#63)]
 [!code-vb[DLinqQueryExamples#63](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#63)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) i *typy anonimowe* do zwrócenia *w kształcie podzestawu* danych dotyczących klientów.  
  
 [!code-csharp[DLinqQueryExamples#64](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#64)]
 [!code-vb[DLinqQueryExamples#64](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#64)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto zapytania zagnieżdżone, aby zostać zwrócone następujące wyniki:  
  
-   Sekwencja wszystkich zleceń i odpowiednie `OrderID`s.  
  
-   Podsekwencji elementów w kolejności, dla którego jest rabat.  
  
-   Ilość pieniędzy zapisany, jeśli nie dołączono kosztu wysyłki.  
  
 [!code-csharp[DLinqQueryExamples#65](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#65)]
 [!code-vb[DLinqQueryExamples#65](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#65)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
