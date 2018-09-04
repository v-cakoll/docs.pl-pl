---
title: Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 5443c409bd3c73e91969db6424a4f86f1a16ed72
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516317"
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR
.NET Framework Data Provider for Oracle obsługuje programu Oracle **REF CURSOR** typu danych. Przy użyciu dostawcy danych do pracy z Oracle REF CURSOR, należy rozważyć następujące zachowania.  
  
> [!NOTE]
>  Niektóre zachowania różnią się od dostawcy Microsoft OLE DB dla Oracle (MSDAORA i).  
  
-   Ze względu na wydajność Data Provider Pro Oracle nie jest automatycznie powiązana **REF CURSOR** typy danych, podobnie jak MSDAORA i, chyba że jawnie określisz je.  
  
-   Dostawca danych nie obsługuje żadnych sekwencje unikowe ODBC, w tym znak ucieczki {resultset} używane do określania parametrów REF CURSOR.  
  
-   Aby wykonać procedurę składowaną, która zwraca kursora REF CURSOR, należy zdefiniować parametry w <xref:System.Data.OracleClient.OracleParameterCollection> z <xref:System.Data.OracleClient.OracleType> z **kursora** i <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **dane wyjściowe**. Dostawca danych obsługuje powiązanie kursora REF CURSOR jako parametry wyjściowe tylko. Dostawca nie obsługuje kursora REF CURSOR jako parametry wejściowe.  
  
-   Uzyskiwanie <xref:System.Data.OracleClient.OracleDataReader> z parametru wartość nie jest obsługiwana. Wartości są typu <xref:System.DBNull> po wykonaniu polecenia.  
  
-   Tylko **commandbehavior ustawiono** wartości wyliczenia, która współdziała z kursora REF CURSOR (na przykład w przypadku, gdy wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) jest **metody**; pozostałe są ignorowane.  
  
-   Kolejność kursora REF CURSOR w **Element OracleDataReader** zależy od rzędu kilku parametrów w **OracleParameterCollection**. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Właściwość jest ignorowana.  
  
-   PL/SQL **tabeli** typ danych nie jest obsługiwany. Jednak kursora REF CURSOR są bardziej wydajne. Jeśli musisz użyć **tabeli** typ danych, należy użyć z MSDAORA i dostawcy OLE DB .NET danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykłady REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Zawiera trzy przykłady demonstrujące użycie kursora REF CURSOR.  
  
 [Parametry kursora REF CURSOR w OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Pokazuje, jak wykonać procedury przechowywanych PL/SQL, zwraca parametr REF CURSOR, która odczytuje wartość jako **Element OracleDataReader**.  
  
 [Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR, a następnie odczytuje wartości za pomocą **Element OracleDataReader**.  
  
 [Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR i wypełnia <xref:System.Data.DataSet> wierszy, które są zwracane.  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
