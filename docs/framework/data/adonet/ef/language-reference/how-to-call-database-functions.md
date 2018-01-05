---
title: "Porady: Wywołaj funkcje bazy danych"
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
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7d385917940e1359b2dc5bef24bb1353db707424
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-database-functions"></a>Porady: Wywołaj funkcje bazy danych
<xref:System.Data.Objects.SqlClient.SqlFunctions> Klasa zawiera metody, które udostępniają funkcje programu SQL Server do użycia w składniku LINQ do jednostek zapytań. Jeśli używasz <xref:System.Data.Objects.SqlClient.SqlFunctions> metody w technologii LINQ do jednostek zapytań, odpowiednie funkcje bazy danych są wykonywane w bazie danych.  
  
> [!NOTE]
>  Funkcje bazy danych, wykonywanie obliczeń na zbiór wartości, które zwraca pojedynczą wartość (znanej także jako funkcje agregujące bazy danych), może być wywoływany bezpośrednio. Inne funkcje canonical można wywołać tylko w ramach zapytania składnika LINQ to Entities. Aby wywołać funkcję agregującą bezpośrednio, należy podać <xref:System.Data.Objects.ObjectQuery%601> funkcji. Aby uzyskać więcej informacji zobacz drugi przykład poniżej.  
  
> [!NOTE]
>  Metody w <xref:System.Data.Objects.SqlClient.SqlFunctions> klasy są specyficzne dla funkcji programu SQL Server. Podobne klas, które udostępniają funkcje bazy danych mogą być dostępne za pośrednictwem innych dostawców.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Przykład wykonuje zapytania składnika LINQ to Entities używającej <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metodę, aby zwrócić wszystkie kontakty, których nazwisko zaczyna się od "Si":  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Przykład wywołuje agregacji <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> metody bezpośrednio. Należy pamiętać, że <xref:System.Data.Objects.ObjectQuery%601> została przekazana do funkcji, co umożliwia można wywołać bez części zapytania składnika LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
