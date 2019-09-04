---
title: Obliczanie sumy wartości w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247926"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Obliczanie sumy wartości w sekwencji numerycznej
Użyj operatora <xref:System.Linq.Enumerable.Sum%2A> , aby obliczyć sumę wartości liczbowych w sekwencji.  
  
 Zwróć uwagę na następujące cechy `Sum` operatora w: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
- Operator `Sum` agregujący standardowego operatora zapytania ma wartość zero dla pustej sekwencji lub sekwencji zawierającej tylko wartości null. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie semantyka SQL pozostaje niezmieniona. Z tego powodu program `Sum` zwraca wartość null zamiast zero dla pustej sekwencji lub dla sekwencji zawierającej tylko wartości null.  
  
- Ograniczenia SQL dotyczące wyników pośrednich stosują się [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]do agregacji w. Suma 32-bitowych liczb całkowitych nie jest obliczana przy użyciu 64-bitowych wyników, a przepełnienie może wystąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w przypadku `Sum`tłumaczenia. Taka możliwość istnieje, nawet jeśli implementacja standardowego operatora zapytań nie powoduje przepełnienia odpowiedniej sekwencji w pamięci.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie łącznego frachtu wszystkich zamówień w `Order` tabeli.  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie łącznej liczby jednostek w kolejności dla wszystkich produktów.  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `780`.  
  
 Należy zauważyć, że należy `short` rzutować typy (na `UnitsOnOrder`przykład) `Sum` , ponieważ nie ma przeciążenia dla krótkich typów.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania zagregowane](aggregate-queries.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
