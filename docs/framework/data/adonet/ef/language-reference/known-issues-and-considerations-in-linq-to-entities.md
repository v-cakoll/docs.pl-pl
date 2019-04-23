---
title: Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 3945d4fc92bea2c4212da0507618203603ae8aba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191331"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Znane problemy i zagadnienia dotyczące składnika LINQ to Entities
Ta sekcja zawiera informacje o znanych problemach z [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
-   [Nie można buforować LINQ zapytań](#LINQQueriesThatAreNotCached)  
  
-   [Kolejność utraty informacji](#OrderingInfoLost)  
  
-   [Liczb całkowitych bez znaku, nie jest obsługiwane](#UnsignedIntsUnsupported)  
  
-   [Błędy konwersji typu](#TypeConversionErrors)  
  
-   [Odwoływanie się do zmiennych nieskalarnego nieobsługiwane](#RefNonScalarClosures)  
  
-   [Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000](#NestedQueriesSQL2000)  
  
-   [Wyświetlanie na typ anonimowy](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>Nie można buforować LINQ zapytań  
 Począwszy od programu .NET Framework 4.5, programu LINQ do jednostek zapytań są automatycznie buforowane. Jednak LINQ do zapytań jednostki, stosowane `Enumerable.Contains` operator z kolekcjami w pamięci nie są automatycznie buforowane. Również parametryzacja kolekcji w skompilowanych zapytań LINQ w pamięci nie jest dozwolone.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Kolejność utraty informacji  
 Projekcji kolumn do typu anonimowego spowoduje, że szeregowania informacje, aby spowodować utratę niektórych kwerend, które są wykonywane względem [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] bazy danych, Ustaw poziom zgodności, "80".  Operacja wykonywana, gdy nazwa kolumny, na liście klauzuli order by pasuje do nazwy kolumny w selektorze, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>Liczb całkowitych bez znaku, nie jest obsługiwane  
 Określanie typu Liczba całkowita bez znaku w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania nie jest obsługiwana, ponieważ [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie obsługuje liczb całkowitych bez znaku. Jeśli określisz liczbę całkowitą bez znaku, <xref:System.ArgumentException> zostanie zgłoszony wyjątek podczas translacji wyrażenie zapytania, jak pokazano w poniższym przykładzie. To przykładowe zapytania dla zamówienia o identyfikatorze 48000.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Błędy konwersji typu  
 W języku Visual Basic, gdy właściwość jest mapowana na kolumnę typu bit programu SQL Server o wartości 1 przy użyciu `CByte` funkcji <xref:System.Data.SqlClient.SqlException> jest zgłaszany z komunikatem "Błąd przepełnienia arytmetycznego". Następujące przykładowe kwerendy `Product.MakeFlag` kolumny w przykładowej bazy danych AdventureWorks i wyjątek jest zgłaszany, gdy wyniki zapytania jest powtarzana.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Odwoływanie się do zmiennych nieskalarnego nieobsługiwane  
 Odwoływanie się do zmiennych nieskalarnego, takich jak jednostki, w zapytaniu nie jest obsługiwane. Gdy jest wykonywana w przypadku takiego zapytania, <xref:System.NotSupportedException> wyjątek z informacją, że komunikat "nie można utworzyć stałej wartości typu `EntityType`. Tylko typy pierwotne ("takie jak Int32, String i Guid") są obsługiwane w tym kontekście."  
  
> [!NOTE]
>  Odwoływanie się do kolekcji zmienne skalarne są obsługiwane.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000  
 Za pomocą programu SQL Server 2000 jednostek zapytaniach składnika LINQ to może się niepowodzeniem, jeśli produkują zagnieżdżonych zapytań języka Transact-SQL, które są co najmniej trzech poziomów w głąb.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Wyświetlanie na typ anonimowy  
 Jeśli zdefiniujesz swoją ścieżkę początkowego zapytania, aby dołączyć powiązane obiekty za pomocą <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metody <xref:System.Data.Objects.ObjectQuery%601> i następnie za pomocą LINQ projektu zwracanych obiektów do typu anonimowego, obiekty w metodzie dołączania nie są uwzględnione w zapytaniu wyniki.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Aby uzyskać powiązane obiekty, nie zwracane typy projektów do typu anonimowego.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
