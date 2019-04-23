---
title: Zapytania skompilowane (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: f3ba6bfd0f83270bc6b9e980fe92f6630c90ad49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193073"
---
# <a name="compiled-queries--linq-to-entities"></a>Zapytania skompilowane (LINQ to Entities)
Jeśli masz aplikację, która wykonuje zapytania strukturalnie podobne wiele razy w programie Entity Framework, często może zwiększyć wydajność, kompilowanie zapytania jeden raz i jej wykonanie kilka razy z różnymi parametrami. Na przykład aplikacja może mieć do pobrania wszystkich klientów określonego miasta; Miasto jest określone w czasie wykonywania przez użytkownika w postaci. Składnik LINQ to Entities obsługuje przy użyciu zapytania skompilowane do tego celu.  
  
 Począwszy od programu .NET Framework 4.5, zapytania LINQ są buforowane automatycznie. Jednak nadal umożliwia zapytania LINQ skompilowane obniżyć ten koszt w późniejszym wykonań i zapytania skompilowane może być bardziej efektywne niż zapytań LINQ, które są automatycznie buforowane. Uwaga składnik LINQ to Entities zapytania, które mają zastosowanie `Enumerable.Contains` operator z kolekcjami w pamięci nie są automatycznie buforowane. Również parametryzacja kolekcji w skompilowanych zapytań LINQ w pamięci nie jest dozwolone.  
  
 <xref:System.Data.Objects.CompiledQuery> Klasa udostępnia kompilacji i pamięci podręcznej zapytań do ponownego wykorzystania. Ta klasa zawiera model <xref:System.Data.Objects.CompiledQuery>firmy `Compile` metody z kilka przeciążeń. Wywołaj `Compile` metodę, aby utworzyć nowe delegowanie do reprezentowania kompilowanym zapytaniu. `Compile` Metod udostępnianych za pomocą <xref:System.Data.Objects.ObjectContext> i wartości parametrów, zwracają obiekt delegowany, który daje wynik, niektóre (takie jak <xref:System.Linq.IQueryable%601> wystąpienie). Zapytanie kompiluje się raz w ciągu pierwszego wykonania. Opcje scalania, ustaw dla zapytania w czasie kompilacji nie można zmienić później. Po kwerendy jest kompilowany można podać tylko parametry typu podstawowego, ale nie można zamienić części zapytania, które spowoduje zmianę wygenerowanych SQL. Aby uzyskać więcej informacji, zobacz [opcje scalania struktury jednostek i kompilowane zapytań](https://go.microsoft.com/fwlink/?LinkId=199591)  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] Wyrażeniu zapytania, <xref:System.Data.Objects.CompiledQuery>firmy `Compile` kompiluje metody jest reprezentowane przez jedną z ogólnych `Func` deleguje odpowiednie uprawnienia, takie jak <xref:System.Func%605>. Co najwyżej umożliwiająca Hermetyzowanie wyrażenia zapytania `ObjectContext` parametr, parametr zwracany i 16 parametry zapytania. Jeśli więcej niż 16 parametry zapytania są wymagane, można utworzyć struktury, których właściwości reprezentują parametry zapytania. Po ustawieniu właściwości można następnie użyć właściwości struktury w wyrażeniu zapytania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompiluje, a następnie wywołuje zapytanie, które akceptuje <xref:System.Decimal> parametr wejściowy i zwraca sekwencję zleceń, których termin łączna liczba jest większa niż lub równa 200,00 $:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje kompilację, a następnie wywołuje zapytanie zwracające <xref:System.Data.Objects.ObjectQuery%601> wystąpienie:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompiluje, a następnie wywołuje zapytanie, które zwraca średnią cen listy produktu jako <xref:System.Decimal> wartość:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompiluje, a następnie wywołuje zapytanie, które akceptuje <xref:System.String> wprowadź parametr, a następnie zwraca `Contact` których adres e-mail zaczyna się od określonego ciągu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompiluje, a następnie wywołuje zapytanie, które akceptuje <xref:System.DateTime> i <xref:System.Decimal> parametry wejściowe i zwraca porządkuje sekwencję, gdzie Data zamówienia jest późniejsza niż 8 marca 2003 i łącznie ze względu jest mniejsza niż 300.00 $:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompiluje, a następnie wywołuje zapytanie, które akceptuje <xref:System.DateTime> parametr wejściowy i zwraca sekwencję zamówienia, w których data zamówienia jest późniejsza niż 8 marca 2004. Ta kwerenda zwraca informacje o zamówieniach jako sekwencja typów anonimowych. Typy anonimowe są wnioskowane przez kompilator, więc nie można określić parametrów typu w <xref:System.Data.Objects.CompiledQuery>firmy `Compile` metoda i typ jest zdefiniowany w samym zapytaniu.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje zapytanie, które akceptuje parametr wejściowy elementu struktury zdefiniowany przez użytkownika i zwraca sekwencję zamówienia. Struktura określa datę rozpoczęcia, Data zakończenia i łącznie ze względu na parametry zapytania, a zapytanie zwróci zamówień wysłanych między 3 marca i 8 marca 2003 z sumą powodu większa niż 700.00 $.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura, która definiuje parametry zapytania:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Opcje scalania w ramach jednostki i zapytania skompilowane](https://go.microsoft.com/fwlink/?LinkId=199591)
