---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 8692dc761f00e0ddc8ec9fad5a5df66b7fda7916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762302"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
<xref:System.Data.Common> Przestrzeń nazw zawiera klasy do tworzenia <xref:System.Data.Common.DbProviderFactory> wystąpień do pracy z konkretnych źródeł danych. Po utworzeniu <xref:System.Data.Common.DbProviderFactory> wystąpienia i przekaż go informacji na temat dostawcy danych `DbProviderFactory` można określić obiektu połączenia poprawny, silnie typizowaną do zwrócenia na podstawie informacji ma zostać podana.  
  
 W programie .NET Framework w wersji 4, dostawców danych, takich jak <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, i <xref:System.Data.OracleClient> nie są wymienione w pliku machine.config, ale niestandardowych dostawców będą nadal wyświetlane istnieje.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie modelu fabryki](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 Zawiera omówienie fabryki wzorca projektowego i interfejs programowania.  
  
 [Uzyskiwanie DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 Pokazuje, jak listy dostawców zainstalowane dane i tworzyć <xref:System.Data.Common.DbConnection> z `DbProviderFactory`.  
  
 [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 Przedstawia sposób tworzenia <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbDataReader>oraz sposób obsługi błędów danych przy użyciu <xref:System.Data.Common.DbException>.  
  
 [Modyfikowanie danych za pomocą obiektu DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 Pokazuje, jak używać <xref:System.Data.Common.DbCommandBuilder> z <xref:System.Data.Common.DbDataAdapter> do pobrania i modyfikowania danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
