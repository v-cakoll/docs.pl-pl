---
title: Skompilowane zapytania (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 37b80a6a7411bc987beb75ebd62778f9589f67e5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="compiled-queries--linq-to-entities"></a>Skompilowane zapytania (LINQ to Entities)
Jeśli masz aplikację, która wykonuje zapytania strukturę podobną wielokrotnie w ramach jednostki często może zwiększyć wydajność kompilacji zapytania jeden raz i jej wykonanie kilka razy z innymi parametrami. Na przykład aplikacje mogą mieć można pobrać wszystkich klientów określonego miasta; miasta określono w czasie wykonywania przez użytkownika w postaci. Składnik LINQ to Entities obsługuje przy użyciu skompilowane zapytania w tym celu.  
  
 Począwszy od programu .NET Framework 4.5, zapytań LINQ są buforowane automatycznie. Jednak nadal umożliwia skompilowane zapytania składnika LINQ to kosztów w późniejszym wykonaniami i skompilowane zapytania może być skuteczniejsza niż zapytań LINQ, które są automatycznie buforowane. Uwaga LINQ to Entities zapytań, które mają zastosowanie `Enumerable.Contains` operator do kolekcji w pamięci nie są automatycznie buforowane. Parametryzacja również kolekcji w pamięci w skompilowanych zapytań LINQ jest niedozwolone.  
  
 <xref:System.Data.Objects.CompiledQuery> Klasa udostępnia kompilacji i buforowanie zapytania do ponownego użycia. Koncepcyjnie, ta klasa zawiera <xref:System.Data.Objects.CompiledQuery>w `Compile` metody z kilka przeciążeń. Wywołanie `Compile` metodę, aby utworzyć nowe delegowanie do reprezentowania kompilowanym zapytaniu. `Compile` Metod udostępnianych z <xref:System.Data.Objects.ObjectContext> i wartości parametrów zwracany delegata, który daje w wyniku niektórych (takich jak <xref:System.Linq.IQueryable%601> wystąpienie). Zapytanie kompiluje raz podczas pierwszego wykonywania. Opcje scalania ustawione dla zapytania w czasie kompilacji nie można zmienić później. Po kompilowania zapytania można podać tylko parametry typu pierwotnego, ale nie można zamienić części zapytania, która zmieniłaby wygenerowanego SQL. Aby uzyskać więcej informacji, zobacz [Entity Framework scalania opcje i skompilowane zapytania](http://go.microsoft.com/fwlink/?LinkId=199591)  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Zapytania wyrażenie który <xref:System.Data.Objects.CompiledQuery>w `Compile` kompiluje metody jest reprezentowane przez jedną z ogólnych `Func` deleguje, takich jak <xref:System.Func%605>. Co najwyżej umożliwiająca Hermetyzowanie wyrażenia zapytania `ObjectContext` parametru, parametr zwrotnego i 16 parametry zapytania. Jeśli więcej niż 16 parametry zapytania są wymagane, można utworzyć struktury, którego właściwości reprezentują parametry zapytania. Po ustawieniu właściwości można następnie użyć właściwości struktury w wyrażeniu zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę, która akceptuje <xref:System.Decimal> parametr wejściowy i zwraca Sekwencja zamówień, w których termin całkowita jest większa niż lub równa $200,00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy, a następnie wywołuje zapytanie zwracające <xref:System.Data.Objects.ObjectQuery%601> wystąpienie:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje zapytanie zwracające średniej ceny listy produktu jako <xref:System.Decimal> wartość:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę, która akceptuje <xref:System.String> danych wejściowych parametru, a następnie zwraca `Contact` których adres e-mail zaczyna się od określonego ciągu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę, która akceptuje <xref:System.DateTime> i <xref:System.Decimal> parametry wejściowe i zwraca sekwencji zlecenia, których data zamówienia jest późniejsza niż 8 marca 2003 i łącznie ze względu jest mniejsza niż 300.00 $:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę, która akceptuje <xref:System.DateTime> parametr wejściowy i zwraca sekwencję zleceń, których data zamówienia jest późniejsza niż 8 marca 2004. Ta kwerenda zwraca informacje o kolejności sekwencję typy anonimowe. Typy anonimowe są wykryta przez kompilator, więc nie można określić parametrów typu w <xref:System.Data.Objects.CompiledQuery>w `Compile` — metoda i typ jest zdefiniowany w samej kwerendzie.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę, która przyjmuje parametr wejściowy struktury zdefiniowane przez użytkownika i zwraca sekwencję zleceń. Struktura definiuje Data rozpoczęcia, Data zakończenia i sum powodu parametry zapytania, a zapytanie zwraca zamówienia między 3 marca i 8 marca 2003 w sumie powodu większa niż 700.00 $.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura, która definiuje parametry zapytania:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Zobacz też  
 [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [Opcje scalania Entity Framework i skompilowane zapytania](http://go.microsoft.com/fwlink/?LinkId=199591)
