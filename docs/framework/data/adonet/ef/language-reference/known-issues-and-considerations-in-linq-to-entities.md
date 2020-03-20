---
title: Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 90119da0fce7a708323d790f91f28206cac0a0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150145"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
Ta sekcja zawiera informacje o znanych problemach z LINQ do kwerend jednostek.  
  
- [Zapytania LINQ, których nie można buforować](#LINQQueriesThatAreNotCached)  
  
- [Zamówienie utraconych informacji](#OrderingInfoLost)  
  
- [Niepodpisane liczby całkowite nie są obsługiwane](#UnsignedIntsUnsupported)  
  
- [Błędy konwersji typu](#TypeConversionErrors)  
  
- [Odwoływanie się do zmiennych nieskawaralnych, które nie są obsługiwane](#RefNonScalarClosures)  
  
- [Zagnieżdżone kwerendy mogą zakończyć się niepowodzeniem w programie SQL Server 2000](#NestedQueriesSQL2000)  
  
- [Rzutowanie typu anonimowego](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>
## <a name="linq-queries-that-cannot-be-cached"></a>Zapytania LINQ, których nie można buforować  
 Począwszy od .NET Framework 4.5, LINQ do jednostek kwerendy są automatycznie buforowane. Jednak LINQ do jednostek kwerend, `Enumerable.Contains` które stosują operatora do kolekcji w pamięci nie są automatycznie buforowane. Również parametryzowanie kolekcji w pamięci w skompilowanych kwerend LINQ jest niedozwolone.  
  
<a name="OrderingInfoLost"></a>
## <a name="ordering-information-lost"></a>Zamówienie utraconych informacji  
 Rzutowanie kolumn na typ anonimowy spowoduje utratę informacji o zamawianiu w niektórych kwerendach wykonywanych w bazie danych programu SQL Server 2005 ustawionej na poziomie zgodności "80".  Dzieje się tak, gdy nazwa kolumny na liście kolejność według pasuje do nazwy kolumny w selektorze, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>
## <a name="unsigned-integers-not-supported"></a>Niepodpisane liczby całkowite nie są obsługiwane  
 Określanie niepodpisanego typu całkowitej w kwerendzie LINQ do jednostek nie jest obsługiwane, ponieważ entity framework nie obsługuje niepodpisanych liczby całkowitej. Jeśli określisz niepodpisaną liczę <xref:System.ArgumentException> całkowitą, podczas tłumaczenia wyrażenia kwerendy zostanie zgłoszony wyjątek, jak pokazano w poniższym przykładzie. W tym przykładzie kwerendy dla zamówienia o identyfikatorze 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>
## <a name="type-conversion-errors"></a>Błędy konwersji typu  
 W języku Visual Basic, gdy właściwość jest mapowana na kolumnę typu `CByte` bitowego <xref:System.Data.SqlClient.SqlException> programu SQL Server o wartości 1 przy użyciu funkcji, a jest generowany z komunikatem "Błąd przepełnienia arytmetycznego". Poniższy przykład kwerendy `Product.MakeFlag` kolumny w adventureworks przykładowej bazy danych i wyjątek jest generowany, gdy wyniki kwerendy są iterowane ponad.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>
## <a name="referencing-non-scalar-variables-not-supported"></a>Odwoływanie się do zmiennych nieskawaralnych, które nie są obsługiwane  
 Odwoływanie się do zmiennych nieskawaralnych, takich jak jednostka, w kwerendzie nie jest obsługiwane. Podczas wykonywania takiej kwerendy <xref:System.NotSupportedException> wyjątek jest zgłaszany z komunikatem "Nie `EntityType`można utworzyć stałej wartości typu. Tylko typy pierwotne ("takie jak Int32, String i Guid") są obsługiwane w tym kontekście."  
  
> [!NOTE]
> Odwołanie się do kolekcji zmiennych skalarnych jest obsługiwane.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Zagnieżdżone kwerendy mogą zakończyć się niepowodzeniem w programie SQL Server 2000  
 Z PROGRAMU SQL Server 2000, LINQ do jednostek kwerendy mogą zakończyć się niepowodzeniem, jeśli produkują zagnieżdżone zapytania Transact-SQL, które są trzy lub więcej poziomów głębokości.  
  
<a name="ProjectToAnonymousType"></a>
## <a name="projecting-to-an-anonymous-type"></a>Rzutowanie typu anonimowego  
 Jeśli zdefiniowano ścieżkę zapytania początkowego, <xref:System.Data.Objects.ObjectQuery%601.Include%2A> aby uwzględnić powiązane obiekty przy użyciu metody <xref:System.Data.Objects.ObjectQuery%601> na, a następnie użyć LINQ do projektu zwracanych obiektów do typu anonimowego, obiekty określone w metody include nie są uwzględniane w wynikach kwerendy.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Aby uzyskać powiązane obiekty, nie projektuj zwrócone typy do typu anonimowego.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Zobacz też

- [LINQ to Entities](linq-to-entities.md)
