---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: e3ea9e3d083314f8df25f9edadbd1a18f1227293
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784100"
---
# <a name="dbproviderfactories"></a>DbProviderFactories
Przestrzeń nazw zawiera klasy służące <xref:System.Data.Common.DbProviderFactory> do tworzenia wystąpień do pracy z określonymi źródłami danych. <xref:System.Data.Common> Po utworzeniu <xref:System.Data.Common.DbProviderFactory> wystąpienia i przejściu do niego informacji o dostawcy `DbProviderFactory` danych można określić poprawny obiekt połączenia o jednoznacznie określonym typie, który ma zostać zwrócony na podstawie dostarczonych informacji.  
  
 Począwszy od .NET Framework w wersji 4, dostawcy danych, takie <xref:System.Data.Odbc>jak <xref:System.Data.OleDb> <xref:System.Data.SqlClient>,, i <xref:System.Data.OracleClient> nie są już wymienione w pliku Machine. config, ale Dostawcy niestandardowi nadal będą wyświetlani w tym miejscu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie modelu fabryki](factory-model-overview.md)  
 Zawiera omówienie wzorca projektowego i interfejsu programowania.  
  
 [Uzyskiwanie DbProviderFactory](obtaining-a-dbproviderfactory.md)  
 Pokazuje, jak wyświetlić listę zainstalowanych dostawców danych i utworzyć <xref:System.Data.Common.DbConnection> `DbProviderFactory`z programu.  
  
 [DbConnection, DbCommand i DbException](dbconnection-dbcommand-and-dbexception.md)  
 Pokazuje, jak utworzyć <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbDataReader>i jak obsługiwać błędy danych przy użyciu programu <xref:System.Data.Common.DbException>.  
  
 [Modyfikowanie danych za pomocą obiektu DbDataAdapter](modifying-data-with-a-dbdataadapter.md)  
 Pokazuje, w jaki sposób <xref:System.Data.Common.DbCommandBuilder> używać elementu <xref:System.Data.Common.DbDataAdapter> with a, aby pobierać i modyfikować dane.  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Omówienie ADO.NET](ado-net-overview.md)
