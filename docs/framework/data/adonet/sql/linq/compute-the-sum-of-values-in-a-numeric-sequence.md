---
title: Obliczanie sumy wartości w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 2f66b996a0e688205d61f5fca476c0335616ee38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032945"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Obliczanie sumy wartości w sekwencji numerycznej
Użyj <xref:System.Linq.Enumerable.Sum%2A> operatora, aby obliczyć sumę wartości liczbowych z sekwencji.  
  
 Należy zwrócić uwagę na następujące cechy `Sum` operatora w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
- Aggregate-operator standardowej kwerendy operatora `Sum` osiągnie wartość zero dla pustej sekwencji lub sekwencję która zawiera tylko wartości null. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], semantyki programu SQL Server są pozostawione bez zmian. Z tego powodu `Sum` daje w wyniku wartość null zamiast zero sekwencję która zawiera tylko wartości null lub pustą sekwencją.  
  
- SQL na wyniki pośrednie ograniczenia wartości zagregowanych umieszczonych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Suma 32-bitowej liczby całkowitej ilości nie jest kolumną obliczaną, za pomocą 64-bitowych wyników i może wystąpić przepełnienie, dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczenia `Sum`. Nawet wtedy, gdy implementacja standardowej kwerendy operatora przepełnienie w odpowiedniej sekwencji w pamięci nie powoduje, że istnieje taka możliwość.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie całkowita transport wszystkich zamówień w `Order` tabeli.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie całkowita liczba jednostek w kolejności dla wszystkich produktów.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `780`.  
  
 Należy zauważyć, że należy rzutować `short` typów (na przykład `UnitsOnOrder`) ponieważ `Sum` ma żadne przeciążenie dla typów krótkich.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania zagregowane](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
