---
title: Mapowanie typu danych w ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 1064f3be7f2548337b5dd6653c76b70a04fad980
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757674"
---
# <a name="data-type-mappings-in-adonet"></a>Mapowanie typu danych w ADO.NET
.NET Framework jest oparta na wspólny system typów, który definiuje sposób typy są zadeklarowany, używane i zarządzane w czasie wykonywania. Zawiera typy wartości i typy referencyjne, które wynikają z <xref:System.Object> typ podstawowy. Podczas pracy ze źródłem danych, wywnioskować typu danych od dostawcy danych, jeśli nie został jawnie określony. Na przykład <xref:System.Data.DataSet> obiektu jest niezależna od wszelkich określonego źródła danych. Dane w `DataSet` jest pobierana ze źródła danych i zmiany są zachowywane do źródła danych przy użyciu `DataAdapter`. Oznacza to, że w przypadku `DataAdapter` wypełnia <xref:System.Data.DataTable> w `DataSet` z wartości ze źródła danych, wynikowy typy danych kolumn w `DataTable` są [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów, zamiast specyficzne dla typów [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] danych Dostawca używany do nawiązania połączenia ze źródłem danych.  
  
 Podobnie, jeśli `DataReader` zwraca wartość ze źródła danych, wynikowej wartości są przechowywane w zmiennej lokalnej, która ma [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Dla obu `Fill` operacji `DataAdapter` i `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu jest wywnioskowany na podstawie wartość zwracana z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych.  
  
 Zamiast polegania na typ danych wykrywany, możesz użyć metody typizowane metody dostępu `DataReader` gdy znasz określonego typu wartości zwracanych. Metody dostępu typu osiągnięcie większej wydajności przez zwrócenie wartości jako określony [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu, co eliminuje konieczność dodatkowy typ konwersji.  
  
> [!NOTE]
>  Wartości null [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy danych dostawcy danych są reprezentowane przez `DBNull.Value`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typu danych serwera SQL](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.SqlClient>.  
  
 [Mapowanie typu danych OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.OleDb>.  
  
 [Mapowanie typu danych ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.Odbc>.  
  
 [Mapowanie typu danych Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metod typu accessor dla <xref:System.Data.OracleClient>.  
  
 [Liczby zmiennoprzecinkowe](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 W tym artykule opisano problemy napotykane przez programistów często podczas pracy z liczb zmiennoprzecinkowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych programu SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [System typu wspólnego](../../../../docs/standard/base-types/common-type-system.md)  
 [Konwertowanie typów](http://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
