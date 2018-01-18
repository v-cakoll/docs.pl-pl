---
title: Kursory REF Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f01ace7bc7dfe1191dac8990210032b60e16f255
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="oracle-ref-cursors"></a>Kursory REF Oracle
.NET Framework Data Provider for Oracle obsługuje programu Oracle **REF CURSOR** — typ danych. Przy użyciu dostawcy danych do pracy z kursorami REF Oracle, należy rozważyć następujące zachowania.  
  
> [!NOTE]
>  Niektóre zachowania różnią się od dostawcy OLE DB firmy Microsoft dla programu Oracle (MSDAORA).  
  
-   Ze względu na wydajność, dostawca danych dla Oracle nie jest automatycznie powiązana **REF CURSOR** typy danych, tak jak w przypadku MSDAORA, chyba że zostaną jawnie określone je.  
  
-   Dostawca danych nie obsługuje żadnych unikowe ODBC, w tym specjalna {zestaw wyników} służy do określania parametrów REF CURSOR.  
  
-   Aby wykonać procedurę składowaną, która zwraca kursory REF, należy zdefiniować parametrów w <xref:System.Data.OracleClient.OracleParameterCollection> z <xref:System.Data.OracleClient.OracleType> z **kursora** i <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **dane wyjściowe**. Dostawca danych obsługuje powiązanie kursory REF jako parametry wyjściowe tylko. Dostawca nie obsługuje kursory REF jako parametry wejściowe.  
  
-   Uzyskiwanie <xref:System.Data.OracleClient.OracleDataReader> z parametru wartość nie jest obsługiwana. Wartości są typu <xref:System.DBNull> po wykonaniu polecenia.  
  
-   Jedynym **CommandBehavior** wartości wyliczenia, który działa z kursorami REF (na przykład podczas wywoływania metody <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) jest **metody**; pozostałe są ignorowane.  
  
-   Kolejność kursory REF w **OracleDataReader** zależy od rzędu parametrów w **OracleParameterCollection**. <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Właściwość jest ignorowana.  
  
-   PL/SQL **tabeli** — typ danych nie jest obsługiwana. Jednak REF kursory są bardziej wydajne. Jeśli musisz użyć **tabeli** typ danych, należy użyć dostawcy OLE DB .NET danych z MSDAORA.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykłady REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Zawiera trzy przykłady ilustrujące przy użyciu kursory REF.  
  
 [Parametry kursora REF CURSOR w OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako **OracleDataReader**.  
  
 [Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR i odczytuje wartości przy użyciu **OracleDataReader**.  
  
 [Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Pokazuje, jak można wykonać procedury przechowywanej PL/SQL, która zwraca dwa parametry REF CURSOR i wpisuje <xref:System.Data.DataSet> z wierszy, które są zwracane.  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle i ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
