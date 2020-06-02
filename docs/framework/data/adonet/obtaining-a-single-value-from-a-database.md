---
title: Uzyskiwanie pojedynczej wartości z bazy danych
description: Dowiedz się, jak zwrócić pojedynczą wartość w ADO.NET. Ten przykładowy kod zwraca wartość kolumny tożsamości dla wstawionego rekordu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286705"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Uzyskiwanie pojedynczej wartości z bazy danych
Może być konieczne zwrócenie informacji o bazie danych, która jest po prostu pojedynczą wartością, a nie w formie tabeli lub strumienia danych. Na przykład możesz chcieć zwrócić wynik funkcji agregującej, takiej jak COUNT ( \* ), sum (Price) lub AVG (ilość). Obiekt **Command** oferuje możliwość zwracania pojedynczych wartości przy użyciu metody **ExecuteScalar** . Metoda **ExecuteScalar** zwraca, jako wartość skalarną, wartość pierwszej kolumny pierwszego wiersza w zestawie wyników.  
  
 Poniższy przykład kodu wstawia nową wartość w bazie danych przy użyciu <xref:System.Data.SqlClient.SqlCommand> . <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>Metoda jest używana do zwracania wartości kolumny Identity dla wstawionego rekordu.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Polecenia i parametry](commands-and-parameters.md)
- [Wykonywanie polecenia](executing-a-command.md)
- [DbConnection, DbCommand i DbException](dbconnection-dbcommand-and-dbexception.md)
- [Omówienie ADO.NET](ado-net-overview.md)
