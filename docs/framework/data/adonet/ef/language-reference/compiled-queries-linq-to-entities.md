---
title: Zapytania skompilowane (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: 2d9df4d479605c0a2514fe30a9150ab7bcfe904e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251154"
---
# <a name="compiled-queries--linq-to-entities"></a>Zapytania skompilowane (LINQ to Entities)
W przypadku aplikacji, która wykonuje zapytania podobne do strukturalnie w Entity Framework, można często zwiększyć wydajność, kompilując zapytanie jeden raz i wykonując je kilka razy z innymi parametrami. Na przykład aplikacja może wymagać pobrania wszystkich klientów z określonego miasta. Miasto jest określone w czasie wykonywania przez użytkownika w formularzu. LINQ to Entities obsługuje w tym celu używanie skompilowanych zapytań.  
  
 Począwszy od .NET Framework 4,5, zapytania LINQ są buforowane automatycznie. Można jednak nadal używać skompilowanych zapytań LINQ, aby ograniczyć ten koszt do późniejszych wykonań, a skompilowane zapytania mogą być bardziej wydajne niż zapytania LINQ, które są automatycznie buforowane. Należy zauważyć, że zapytania LINQ to Entities, `Enumerable.Contains` które stosują operator do kolekcji w pamięci, nie są automatycznie buforowane. Parametryzacja również kolekcje w pamięci w skompilowanych zapytaniach LINQ są niedozwolone.  
  
 <xref:System.Data.Objects.CompiledQuery> Klasa zawiera kompilację i buforowanie zapytań do ponownego użycia. Koncepcyjnie, ta klasa zawiera <xref:System.Data.Objects.CompiledQuery> `Compile` metodę z kilkoma przeciążeniami. Wywołaj `Compile` metodę, aby utworzyć nowy delegat reprezentujący skompilowane zapytanie. Metody, dostarczone <xref:System.Data.Objects.ObjectContext> z wartościami parametrów i zwracają delegata, który tworzy jakiś <xref:System.Linq.IQueryable%601> wynik (na przykład wystąpienie). `Compile` Zapytanie kompiluje się raz podczas pierwszego wykonania. Opcji scalania ustawionych dla zapytania w czasie kompilacji nie można później zmienić. Po skompilowaniu zapytania można dostarczyć tylko parametry typu pierwotnego, ale nie można zastąpić części zapytania, które mogłyby spowodować zmianę wygenerowanej bazy danych SQL. Aby uzyskać więcej informacji, zobacz [Entity Framework opcje scalania i skompilowane zapytania](https://go.microsoft.com/fwlink/?LinkId=199591)  
  
 Wyrażenie <xref:System.Data.Objects.CompiledQuery>zapytania LINQ to Entities, które `Compile` jest kompilowane Metoda jest reprezentowane przez jeden z delegatów ogólnych `Func` , takich jak <xref:System.Func%605>. Co więcej, wyrażenie zapytania może hermetyzować `ObjectContext` parametr, parametr Return i 16 parametrów zapytania. Jeśli wymagane są więcej niż 16 parametrów zapytania, można utworzyć strukturę, której właściwości reprezentują parametry zapytania. Po ustawieniu właściwości można użyć właściwości struktury w wyrażeniu zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje zapytanie, które akceptuje <xref:System.Decimal> parametr wejściowy i zwraca sekwencję zamówień, w których całkowita liczba operacji jest większa lub równa $200,00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje zapytanie zwracające <xref:System.Data.Objects.ObjectQuery%601> wystąpienie:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje zapytanie, które zwraca średnią cen z listy produktów jako <xref:System.Decimal> wartość:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę akceptującą <xref:System.String> parametr wejściowy, a następnie zwraca wartość, `Contact` której adres e-mail rozpoczyna się od określonego ciągu:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę akceptującą <xref:System.DateTime> i <xref:System.Decimal> wejściową parametrów oraz zwraca sekwencję zamówień, w których Data zamówienia jest późniejsza niż 8 marca 2003, a łączna kwota jest mniejsza niż $300,00:  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę akceptującą <xref:System.DateTime> parametr wejściowy i zwraca sekwencję zamówień, w których Data zamówienia jest późniejsza niż 8 marca 2004. To zapytanie zwraca informacje o kolejności jako sekwencję typów anonimowych. Typy anonimowe są wywnioskowane przez kompilator, dlatego nie można określić parametrów typu w <xref:System.Data.Objects.CompiledQuery> `Compile` metodzie, a typ jest zdefiniowany w zapytaniu.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje, a następnie wywołuje kwerendę akceptującą parametr wejściowy struktury zdefiniowanej przez użytkownika i zwraca sekwencję zamówień. Struktura definiuje datę początkową, datę końcową i łączną liczbę parametrów zapytania, a zapytanie zwraca zamówienia wysłane między 3 marca i 8 marca 2003 ze wszystkimi wynikami przekraczającymi $700,00.  
  
 [!code-csharp[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples#CompiledQuery7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 Struktura, która definiuje parametry zapytania:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples#MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../index.md)
- [LINQ to Entities](linq-to-entities.md)
- [Entity Framework opcje scalania i skompilowane zapytania](https://go.microsoft.com/fwlink/?LinkId=199591)
