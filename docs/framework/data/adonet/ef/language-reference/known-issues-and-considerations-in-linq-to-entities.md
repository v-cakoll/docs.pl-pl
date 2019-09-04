---
title: Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 7be3491af48ad29cd7892dd31a077aa7ac44ca63
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250497"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
Ta sekcja zawiera informacje o znanych problemach dotyczących LINQ to Entities zapytań.  
  
- [Zapytania LINQ, które nie mogą być buforowane](#LINQQueriesThatAreNotCached)  
  
- [Utracone informacje o uporządkowaniu](#OrderingInfoLost)  
  
- [Liczby całkowite bez znaku są nieobsługiwane](#UnsignedIntsUnsupported)  
  
- [Błędy konwersji typów](#TypeConversionErrors)  
  
- [Odwołania do zmiennych nieskalarnych nie są obsługiwane](#RefNonScalarClosures)  
  
- [Zapytania zagnieżdżone mogą zakończyć się niepowodzeniem z SQL Server 2000](#NestedQueriesSQL2000)  
  
- [Projekcja do typu anonimowego](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>Zapytania LINQ, które nie mogą być buforowane  
 Począwszy od .NET Framework 4,5, zapytania LINQ to Entities są buforowane automatycznie. Jednak LINQ to Entities zapytania, które stosują `Enumerable.Contains` operator do kolekcji w pamięci, nie są automatycznie buforowane. Parametryzacja również kolekcje w pamięci w skompilowanych zapytaniach LINQ są niedozwolone.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Utracone informacje o uporządkowaniu  
 Projekcja kolumn na typ anonimowy spowoduje utratę informacji o uporządkowaniu w niektórych zapytaniach, które są wykonywane w odniesieniu do bazy danych SQL Server 2005 z ustawionym poziomem zgodności równym "80".  Dzieje się tak, gdy nazwa kolumny w liście order by jest zgodna z nazwą kolumny w selektorze, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>Liczby całkowite bez znaku są nieobsługiwane  
 Określanie typu liczby całkowitej bez znaku w zapytaniu LINQ to Entities nie jest obsługiwane, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ponieważ nie obsługuje liczb całkowitych bez znaku. Jeśli określisz liczbę całkowitą bez znaku, <xref:System.ArgumentException> podczas tłumaczenia wyrażenia zapytania zostanie zgłoszony wyjątek, jak pokazano w poniższym przykładzie. To przykładowe zapytanie dla zamówienia o IDENTYFIKATORze 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Błędy konwersji typów  
 W Visual Basic, gdy właściwość jest zamapowana do kolumny typu SQL Server bitowego o wartości 1 przy użyciu `CByte` funkcji <xref:System.Data.SqlClient.SqlException> , jest generowany z komunikatem "błąd przepełnienia arytmetycznego". Poniższy przykład wysyła zapytanie do `Product.MakeFlag` kolumny w przykładowej bazie danych AdventureWorks, a wyjątek jest zgłaszany, gdy wyniki zapytania są powtarzane.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Odwołania do zmiennych nieskalarnych nie są obsługiwane  
 Odwoływanie się do zmiennych nieskalarnych, takich jak jednostka, w zapytaniu nie jest obsługiwane. Gdy takie zapytanie jest wykonywane, <xref:System.NotSupportedException> zostanie zgłoszony wyjątek z komunikatem informującym o tym, że nie można utworzyć stałej wartości typu. `EntityType` W tym kontekście są obsługiwane tylko typy pierwotne (takie jak Int32, String i GUID). "  
  
> [!NOTE]
> Obsługiwane jest odwołanie do kolekcji zmiennych skalarnych.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Zapytania zagnieżdżone mogą zakończyć się niepowodzeniem z SQL Server 2000  
 W przypadku SQL Server 2000 zapytania LINQ to Entities mogą zakończyć się niepowodzeniem, jeśli generują zagnieżdżone zapytania Transact-SQL, które są trzy lub więcej poziomów głębokości.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Projekcja do typu anonimowego  
 W przypadku zdefiniowania początkowej ścieżki zapytania w celu uwzględnienia pokrewnych <xref:System.Data.Objects.ObjectQuery%601.Include%2A> obiektów przy użyciu <xref:System.Data.Objects.ObjectQuery%601> metody w programie, a następnie użycie LINQ do zaprojektowania zwracanych obiektów do typu anonimowego, obiekty określone w metodzie include nie zostaną uwzględnione w zapytaniu uzyskane.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Aby uzyskać powiązane obiekty, nie należy projektować zwracanych typów do typu anonimowego.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Entities](linq-to-entities.md)
