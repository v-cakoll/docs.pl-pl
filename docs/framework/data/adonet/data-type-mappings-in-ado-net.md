---
title: Mapowanie typu danych w ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: aba1eb4fdaaf43d66337ca764fe01b7d3f4624bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516930"
---
# <a name="data-type-mappings-in-adonet"></a>Mapowanie typu danych w ADO.NET
.NET Framework jest oparty na wspólny system typów definiuje, jak typy są deklarowane, używane i zarządzane w środowisku uruchomieniowym. Składa się z typami wartości i typami odwołań, które wynikają z <xref:System.Object> typ podstawowy. Podczas pracy ze źródłem danych, typ danych jest wnioskowany z dostawcy danych, jeśli nie jest jawnie określona. Na przykład <xref:System.Data.DataSet> obiektu jest niezależna od wszelkich określonego źródła danych. Dane w `DataSet` jest pobierany ze źródła danych, a zmiany są utrwalane w źródle danych przy użyciu `DataAdapter`. Oznacza to, że w przypadku `DataAdapter` wypełnia <xref:System.Data.DataTable> w `DataSet` wartościami ze źródła danych, wynikowy typy danych kolumn w `DataTable` są [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów, zamiast specyficzne dla typów [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] danych Dostawca, który jest używany do połączenia ze źródłem danych.  
  
 Podobnie, gdy `DataReader` zwraca wartość z zakresu od źródła danych, wartość wynikowa znajduje się w zmiennej lokalnej, która ma [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu. Dla obu `Fill` operacji `DataAdapter` i `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ jest wnioskowany z wartości zwracanej z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych.  
  
 Zamiast polegania na typ danych wykrywany, możesz użyć metody typizowane metody dostępu `DataReader` Jeśli znasz już określonego typu wartości zwracanych. Metody dostępu wpisane zapewniają lepszą wydajność, zwracając wartość jako określony [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ, który eliminuje potrzebę stosowania dodatkowy typ konwersji.  
  
> [!NOTE]
>  Wartość null, wartości [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy danych dostawcy danych są reprezentowane przez `DBNull.Value`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typu danych serwera SQL](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metody dostępu dla <xref:System.Data.SqlClient>.  
  
 [Mapowanie typu danych OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metody dostępu dla <xref:System.Data.OleDb>.  
  
 [Mapowanie typu danych ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metody dostępu dla <xref:System.Data.Odbc>.  
  
 [Mapowanie typu danych Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Wyświetla wywnioskować mapowanie typu danych i danych metody dostępu dla <xref:System.Data.OracleClient>.  
  
 [Liczby zmiennoprzecinkowe](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 W tym artykule opisano problemy, które deweloperzy często występują podczas pracy z liczb zmiennoprzecinkowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych programu SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Konfigurowanie parametrów i typów danych parametrów](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [System typu wspólnego](../../../../docs/standard/base-types/common-type-system.md)  
 [Konwertowanie typów](https://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
