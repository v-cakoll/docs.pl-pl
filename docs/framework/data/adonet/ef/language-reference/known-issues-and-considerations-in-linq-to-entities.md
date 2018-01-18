---
title: "Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: dd45bc4f2229237c50e9bfda36e5fb18512f9ef0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a>Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities
Ta sekcja zawiera informacje o znanych problemach z [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
-   [Nie można buforować LINQ kwerend czy](#LINQQueriesThatAreNotCached)  
  
-   [Porządkowanie utraty informacji](#OrderingInfoLost)  
  
-   [Liczb całkowitych bez znaku, które nie są obsługiwane](#UnsignedIntsUnsupported)  
  
-   [Błędy konwersji typu](#TypeConversionErrors)  
  
-   [Tworzenie odwołań nie są obsługiwane zmienne nieskalarnego](#RefNonScalarClosures)  
  
-   [Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000](#NestedQueriesSQL2000)  
  
-   [Projekcji do typu anonimowego](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>   
## <a name="linq-queries-that-cannot-be-cached"></a>Nie można buforować LINQ kwerend czy  
 Począwszy od programu .NET Framework 4.5, składnika LINQ to Entities zapytania są automatycznie buforowane. Jednak LINQ do jednostek zapytań, które są stosowane `Enumerable.Contains` operator do kolekcji w pamięci nie są automatycznie buforowane. Parametryzacja również kolekcji w pamięci w skompilowanych zapytań LINQ jest niedozwolone.  
  
<a name="OrderingInfoLost"></a>   
## <a name="ordering-information-lost"></a>Porządkowanie utraty informacji  
 Projekcji kolumny typu anonimowego spowoduje, że porządkowania informacje, aby spowodować utratę niektórych kwerend, które są wykonywane przed [!INCLUDE[ssVersion2005](../../../../../../includes/ssversion2005-md.md)] bazy danych Ustaw poziom zgodności "80".  Występuje, gdy nazwa kolumny w liście order by odpowiada nazwie kolumny w selektorze, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>   
## <a name="unsigned-integers-not-supported"></a>Liczb całkowitych bez znaku, które nie są obsługiwane  
 Określanie typu Liczba całkowita bez znaku w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania nie jest obsługiwana, ponieważ [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] nie obsługuje liczb całkowitych bez znaku. Jeśli określisz całkowitą bez znaku <xref:System.ArgumentException> zostanie wygenerowany wyjątek podczas tłumaczenia wyrażenia zapytania, jak pokazano w poniższym przykładzie. To przykładowe zapytania o identyfikatorze 48000 zamówienia.  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>   
## <a name="type-conversion-errors"></a>Błędy konwersji typu  
 W języku Visual Basic, gdy właściwość jest zamapowana na kolumnę typu bit programu SQL Server o wartości 1 przy użyciu `CByte` funkcji <xref:System.Data.SqlClient.SqlException> jest zgłaszany z komunikatem "Błąd przepełnienia arytmetycznego". Następujące przykładowe zapytania `Product.MakeFlag` kolumny przykładową bazę danych AdventureWorks i wyjątek jest generowany, gdy wyniki zapytania są iterowane za pośrednictwem.  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>   
## <a name="referencing-non-scalar-variables-not-supported"></a>Tworzenie odwołań nie są obsługiwane zmienne nieskalarnego  
 Odwołanie do zmiennych nieskalarnego, takich jak jednostki w zapytaniu nie jest obsługiwane. Podczas takiej kwerendy, <xref:System.NotSupportedException> wyjątku z komunikat "nie można utworzyć wartości stałej typu `EntityType`. Tylko typy pierwotne ("takie jak Int32, typ String i identyfikator Guid") są obsługiwane w tym kontekście."  
  
> [!NOTE]
>  Odwołanie do kolekcji zmienne skalara jest obsługiwana.  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>   
## <a name="nested-queries-may-fail-with-sql-server-2000"></a>Zapytania zagnieżdżone może zakończyć się niepowodzeniem z programem SQL Server 2000  
 Programu SQL Server 2000 Jeśli wygenerowanie zagnieżdżonych zapytań języka Transact-SQL, które są co najmniej trzech poziomów w głąb może nie powieść składnika LINQ to Entities zapytania.  
  
<a name="ProjectToAnonymousType"></a>   
## <a name="projecting-to-an-anonymous-type"></a>Projekcji do typu anonimowego  
 Jeśli zdefiniujesz ścieżki początkowego zapytania zawierają obiekty powiązane przy użyciu <xref:System.Data.Objects.ObjectQuery%601.Include%2A> metoda <xref:System.Data.Objects.ObjectQuery%601> , a następnie za pomocą LINQ projektu zwracanych obiektów do typu anonimowego, obiektów w metodzie include nie są uwzględnione w zapytaniu wyniki.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 Aby uzyskać powiązanych obiektów, nie projektu zwracanych typów do typu anonimowego.  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
