---
title: Uzyskiwanie pojedynczej wartości z bazy danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 5eb81fd2a64f06f1252f71e251e58df568e7407c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772076"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Uzyskiwanie pojedynczej wartości z bazy danych
Może być konieczne o zwracanym bazy danych, które są po prostu pojedynczej wartości, a nie w formie strumienia tabeli lub danych. Na przykład możesz chcieć zwracają wynik funkcji agregującej, takie jak liczba (\*), SUM(Price) lub AVG(Quantity). **Polecenia** obiekt umożliwia zwracanie wartości pojedynczej przy użyciu **ExecuteScalar** metody. **ExecuteScalar** metoda zwróci wartość, jako wartość skalarną, wartość pierwszą kolumnę pierwszego wiersza w zestawie wyników.  
  
 Poniższy przykład kodu Wstawia nową wartość w bazie danych przy użyciu <xref:System.Data.SqlClient.SqlCommand>. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda służy do zwracania wartości kolumny tożsamości dla wstawionego rekordu.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)
- [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
