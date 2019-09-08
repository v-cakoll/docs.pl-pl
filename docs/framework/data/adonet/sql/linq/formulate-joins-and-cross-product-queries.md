---
title: Formułowanie połączeń i zapytań między produktami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 002a644ff5d48b25351228dcd74330707491d6c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782093"
---
# <a name="formulate-joins-and-cross-product-queries"></a>Formułowanie połączeń i zapytań między produktami
W poniższych przykładach pokazano, jak połączyć wyniki z wielu tabel.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa nawigacji klucza obcego w `From` klauzuli w Visual Basic (`from` klauzula in C#), aby wybrać wszystkie zamówienia dla klientów w Londynie.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest używana Nawigacja klucza obcego w `Where` klauzuli w Visual Basic (`where` klauzula in C#), aby odfiltrować elementy poza `Products` magazynem `Supplier` , których wartość znajduje się w Stany Zjednoczone.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa nawigacji klucza obcego w `From` klauzuli w Visual Basic (`from` klauzula in C#), aby odfiltrować pracowników w Seattle i wyświetlić listę ich terytoriów.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest używana Nawigacja klucza obcego w `Select` klauzuli w Visual Basic (`select` klauzula in C#), aby odfiltrować pary pracowników, w których jeden pracownik raportuje do drugiego i gdzie oba pracownicy są `City`z tego samego.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Przykład  
 Poniższy Visual Basic przykład szuka wszystkich klientów i zamówień, upewnia się, że zamówienia są dopasowane do klientów i gwarantuje, że dla każdego klienta na tej liście zostanie podana nazwa kontaktu.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jawnie łączy dwie tabele i projekty w obu tabelach.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład jawnie sprzęga trzy tabele i projekty z każdego z nich.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak osiągnąć `LEFT OUTER JOIN` za pomocą. `DefaultIfEmpty()` Metoda zwraca wartość null, `Employee`Jeśli nie `Order` ma dla elementu. `DefaultIfEmpty()`  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy w `let` projekcie wyrażenie wynikłe z sprzężenia.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia `join` z kluczem złożonym.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć `join` miejsce, gdzie jedna strona ma wartość null, a druga nie.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
