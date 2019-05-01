---
title: Formułowanie połączeń i zapytań między produktami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: b0037f56947a86627ee9ea84369527aec859a0f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032607"
---
# <a name="formulate-joins-and-cross-product-queries"></a>Formułowanie połączeń i zapytań między produktami
Poniższe przykłady pokazują, jak połączyć wyniki z wielu tabel.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `From` klauzuli w języku Visual Basic (`from` w klauzuli C#) aby wybrać wszystkie zamówienia dla klientów w Londynie.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `Where` klauzuli w języku Visual Basic (`where` w klauzuli C#) do filtrowania typu "out akcji" `Products` którego `Supplier` znajduje się w Stanach Zjednoczonych.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `From` klauzuli w języku Visual Basic (`from` w klauzuli C#) do filtrowania dla pracowników w Seattle i aby wyświetlić listę swoich obszarów.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto obcego klucza nawigacji w `Select` klauzuli w języku Visual Basic (`select` w klauzuli C#) do filtrowania dla par pracowników, gdzie jednego pracownika raporty do drugiego i gdzie jest taka sama zarówno pracowników `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie w języku Visual Basic szuka wszystkich klientów i zamówień, upewnia się, że zamówienia są dopasowywane do klientów i gwarantuje, że dla każdego klienta na tej liście podano nazwę kontaktu.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy sprzężenie jawnie dwóch projektów i tabel wyników z obu tabel.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy sprzężenie jawnie trzy tabele i projekty wyniki z każdej z nich.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak osiągnąć `LEFT OUTER JOIN` przy użyciu `DefaultIfEmpty()`. `DefaultIfEmpty()` Metoda zwraca wartość null, gdy istnieje nie `Order` dla `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe projekty `let` wyrażenie wynikiem sprzężenia.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `join` przy użyciu klucza złożonego.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonstruować `join` gdzie jednej strony ma wartość null, a druga nie.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
