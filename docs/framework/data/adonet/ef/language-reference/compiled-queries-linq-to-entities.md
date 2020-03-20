---
title: Zapytania skompilowane (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 97ceef3377a67fc621a097843abade9c61c29ca1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848772"
---
# <a name="compiled-queries--linq-to-entities"></a>Zapytania skompilowane (LINQ to Entities)
Jeśli masz aplikację, która wykonuje strukturalnie podobne zapytania wiele razy w entity framework, często można zwiększyć wydajność, kompilując kwerendę jeden raz i wykonując go kilka razy z różnymi parametrami. Na przykład aplikacja może być konieczności pobierania wszystkich klientów w określonym mieście; miasto jest określone w czasie wykonywania przez użytkownika w formularzu. LINQ do jednostek obsługuje przy użyciu skompilowanych zapytań w tym celu.  
  
 Począwszy od programu .NET Framework 4.5, zapytania LINQ są buforowane automatycznie. Jednak nadal można użyć skompilowanych zapytań LINQ, aby zmniejszyć ten koszt w późniejszych wykonaniach i skompilowanych kwerend może być bardziej wydajne niż zapytania LINQ, które są automatycznie buforowane. Należy zauważyć, że LINQ do `Enumerable.Contains` jednostek kwerendy, które stosują operatora do kolekcji w pamięci nie są automatycznie buforowane. Również parametryzowanie kolekcji w pamięci w skompilowanych kwerend LINQ jest niedozwolone.  
  
 Klasa <xref:System.Data.Objects.CompiledQuery> zapewnia kompilacji i buforowania kwerend do ponownego użycia. Koncepcyjnie ta <xref:System.Data.Objects.CompiledQuery>klasa `Compile` zawiera metodę 's z kilkoma przeciążeniami. Wywołanie `Compile` metody, aby utworzyć nowego pełnomocnika do reprezentowania skompilowane zapytanie. Metody, `Compile` dostarczone z <xref:System.Data.Objects.ObjectContext> wartościami i parametrami, zwracają delegata, <xref:System.Linq.IQueryable%601> który daje pewne wyniki (takie jak wystąpienie). Kwerenda kompiluje się raz podczas tylko pierwszego wykonania. Opcji scalania ustawionych dla kwerendy w czasie kompilacji nie można później zmienić. Po skompilowaniu kwerendy można podać tylko parametry typu pierwotnego, ale nie można zastąpić części kwerendy, które mogłyby zmienić wygenerowany SQL. Aby uzyskać więcej informacji, zobacz [Opcje korespondencji seryjnej EF i Skompilowane kwerendy](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries).
  
 Linq do jednostek zapytanie <xref:System.Data.Objects.CompiledQuery>wyrażenie, które skompiluje `Compile` metoda `Func` jest reprezentowana <xref:System.Func%605>przez jednego z delegatów rodzajowych, takich jak . Co najwyżej wyrażenie kwerendy może hermetyzować `ObjectContext` parametr, parametr zwracany i 16 parametrów kwerendy. Jeśli wymagane jest więcej niż 16 parametrów kwerendy, można utworzyć strukturę, której właściwości reprezentują parametry kwerendy. Następnie można użyć właściwości struktury w wyrażeniu kwerendy po ustawieniu właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje <xref:System.Decimal> kwerendę, która akceptuje parametr wejściowy i zwraca sekwencję zamówień, w których całkowita należność jest większa lub równa $200.00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie <xref:System.Data.Objects.ObjectQuery%601> wywołuje kwerendę, która zwraca wystąpienie:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę, która <xref:System.Decimal> zwraca średnią cen listy produktów jako wartość:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje <xref:System.String> kwerendę, która `Contact` akceptuje parametr wejściowy, a następnie zwraca, którego adres e-mail rozpoczyna się od określonego ciągu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie <xref:System.DateTime> wywołuje <xref:System.Decimal> kwerendę, która akceptuje i wprowadzania parametrów i zwraca sekwencję zamówień, gdzie data zamówienia jest późniejsza niż 8 marca 2003 r., a całkowita należność jest mniejsza niż $300.00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje <xref:System.DateTime> kwerendę, która akceptuje parametr wejściowy i zwraca sekwencję zamówień, w której data zamówienia jest późniejsza niż 8 marca 2004. Ta kwerenda zwraca informacje o kolejności jako sekwencję typów anonimowych. Typy anonimowe są wywnioskowane przez kompilator, więc nie można określić parametry typu w metodzie <xref:System.Data.Objects.CompiledQuery>'s `Compile` i typ jest zdefiniowany w samej kwerendzie.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę, która akceptuje parametr wejściowy struktury zdefiniowanej przez użytkownika i zwraca sekwencję zamówień. Struktura definiuje datę rozpoczęcia, datę zakończenia i całkowite parametry kwerendy due, a kwerenda zwraca zamówienia wysłane między 3 marca a 8 marca 2003 r. o łącznej wartości należnej większej niż 700,00 USD.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura definiująca parametry kwerendy:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Zobacz też

- [Program Entity Framework na platformie ADO.NET](../index.md)
- [LINQ to Entities](linq-to-entities.md)
- [Opcje scalania EF i skompilowane kwerendy](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
