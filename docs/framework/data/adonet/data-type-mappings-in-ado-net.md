---
title: Mapowanie typu danych w ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: ddb3c1c5551336ace66bab53af3beb83b6cd2d34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950399"
---
# <a name="data-type-mappings-in-adonet"></a>Mapowanie typu danych w ADO.NET
.NET Framework opiera się na wspólnym typie systemu, który definiuje, w jaki sposób typy są zadeklarowane, używane i zarządzane w czasie wykonywania. Składa się z obu typów wartości i typów referencyjnych, które pochodzą z <xref:System.Object> typu podstawowego. Podczas pracy ze źródłem danych typ danych jest wnioskowany od dostawcy danych, jeśli nie został jawnie określony. Na przykład <xref:System.Data.DataSet> obiekt jest niezależny od określonego źródła danych. Dane z `DataAdapter`programu sąpobieranezeźródładanych,azmianysąutrwalanewźródle`DataSet` danych przy użyciu. Oznacza to, że podczas `DataAdapter` wypełniania a `DataSet` <xref:System.Data.DataTable> w wartości z wartościami ze źródła danych, `DataTable` wyniki typów danych kolumn w są .NET Framework typy, a nie typy specyficzne dla dostawcy danych .NET Framework, który służy do nawiązywania połączenia ze źródłem danych.  
  
 Podobnie, gdy `DataReader` zwraca wartość ze źródła danych, wynikowa wartość jest przechowywana w zmiennej lokalnej, która ma typ .NET Framework. `Fill` Dla operacji `DataAdapter` i`Get` metod ,typ.NETFrameworkjestwywnioskowanynapodstawiewartościzwróconejprzezdostawcędanych.NETFramework.`DataReader`  
  
 Zamiast polegać na wywnioskowanym typie danych, można użyć typów metod dostępu typu w `DataReader` przypadku, gdy wiadomo, że określony typ zwracanej wartości. Wpisywane metody dostępu zapewniają lepszą wydajność, zwracając wartość jako określony typ .NET Framework, co eliminuje konieczność stosowania dodatkowej konwersji typu.  
  
> [!NOTE]
> Wartości null dla typów danych .NET Framework dostawcy danych są reprezentowane przez `DBNull.Value`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typu danych serwera SQL](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.SqlClient>dla programu.  
  
 [Mapowanie typu danych OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.OleDb>dla programu.  
  
 [Mapowanie typu danych ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.Odbc>dla programu.  
  
 [Mapowanie typu danych Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.OracleClient>dla programu.  
  
 [Liczby zmiennoprzecinkowe](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Opisuje problemy, które deweloperzy często napotykają podczas pracy z liczbami zmiennoprzecinkowymi.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych programu SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Konfigurowanie parametrów i typów danych parametrów](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Pobieranie informacji o schemacie bazy danych](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [System typu wspólnego](../../../standard/base-types/common-type-system.md)
- [Konwertowanie typów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
