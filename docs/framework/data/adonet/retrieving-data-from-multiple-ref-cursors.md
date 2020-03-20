---
title: Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 361e9bd4-447d-44b7-8629-3c11f1a7ffbb
ms.openlocfilehash: 8ece2617dd81161cb19a08d62f14d37c0f8c1f33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149040"
---
# <a name="retrieving-data-from-multiple-ref-cursors-using-an-oracledatareader"></a><span data-ttu-id="c21c8-102">Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="c21c8-102">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>
<span data-ttu-id="c21c8-103">W tym przykładzie programu Microsoft Visual Basic wykonuje procedurę składowaną PL/SQL, która <xref:System.Data.OracleClient.OracleDataReader>zwraca dwa parametry REF CURSOR i odczytuje wartości za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="c21c8-103">This Microsoft Visual Basic example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
```vb  
Private Sub Button1_Click( _  
  ByVal sender As Object, ByVal e As System.EventArgs)  _  
  Handles Button1.Click  
  
  Dim connString As New String( _  
      "Data Source=Oracle9i;User ID=scott;Password=tiger;")  
  Using conn As New OracleConnection(connString)  
    Dim cmd As New OracleCommand()  
    Dim rdr As OracleDataReader  
  
    conn.Open()  
    cmd.Connection = conn  
    cmd.CommandText = "CURSPKG.OPEN_TWO_CURSORS"  
    cmd.CommandType = CommandType.StoredProcedure  
    cmd.Parameters.Add(New OracleParameter( _  
      "EMPCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
    cmd.Parameters.Add(New OracleParameter(_  
      "DEPTCURSOR", OracleType.Cursor)).Direction = _  
      ParameterDirection.Output  
  
    rdr = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
    While (rdr.Read())  
        REM do something with the values from the EMP table
    End While  
  
    rdr.NextResult()  
    While (rdr.Read())  
        REM do something with the values from the DEPT table
    End While  
    rdr.Close()  
  End Using  
End Sub
```  
  
## <a name="see-also"></a><span data-ttu-id="c21c8-104">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c21c8-104">See also</span></span>

- [<span data-ttu-id="c21c8-105">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="c21c8-105">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="c21c8-106">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c21c8-106">ADO.NET Overview</span></span>](ado-net-overview.md)
