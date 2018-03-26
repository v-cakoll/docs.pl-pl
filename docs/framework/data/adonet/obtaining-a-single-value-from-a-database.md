---
title: Uzyskiwanie pojedynczą wartość z bazy danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 41c3547d203a9958d3ad84303469c1e9591e6bd3
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="obtaining-a-single-value-from-a-database"></a>Uzyskiwanie pojedynczą wartość z bazy danych
Informacje o zwracany bazy danych, które są po prostu pojedynczą wartość, a nie w formie tabeli lub strumień danych może być konieczne. Na przykład można zwrócić wyników funkcji agregującej, takie jak liczba (\*), SUM(Price) lub AVG(Quantity). **Polecenia** obiektu oferuje możliwość zwrócić jednej wartości przy użyciu **ExecuteScalar** metody. **ExecuteScalar** metoda zwróci wartość, jako wartość skalarną, wartość pierwszą kolumnę pierwszego wiersza w zestawie wyników.  
  
 Poniższy przykład kodu Wstawia nową wartość w bazie danych przy użyciu <xref:System.Data.SqlClient.SqlCommand>. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda służy do zwracania wartości kolumny tożsamości wstawionego rekordu.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
