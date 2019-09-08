---
title: Mapowanie typu danych w ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 9c0d19f724c1876f7dac86055bed2ef77ac76a77
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785591"
---
# <a name="data-type-mappings-in-adonet"></a>Mapowanie typu danych w ADO.NET
.NET Framework opiera się na wspólnym typie systemu, który definiuje, w jaki sposób typy są zadeklarowane, używane i zarządzane w czasie wykonywania. Składa się z obu typów wartości i typów referencyjnych, które pochodzą z <xref:System.Object> typu podstawowego. Podczas pracy ze źródłem danych typ danych jest wnioskowany od dostawcy danych, jeśli nie został jawnie określony. Na przykład <xref:System.Data.DataSet> obiekt jest niezależny od określonego źródła danych. Dane z `DataAdapter`programu sąpobieranezeźródładanych,azmianysąutrwalanewźródle`DataSet` danych przy użyciu. Oznacza to, że podczas `DataAdapter` wypełniania a `DataSet` <xref:System.Data.DataTable> w wartości z wartościami ze źródła danych, `DataTable` wyniki typów danych kolumn w są .NET Framework typy, a nie typy specyficzne dla dostawcy danych .NET Framework, który służy do nawiązywania połączenia ze źródłem danych.  
  
 Podobnie, gdy `DataReader` zwraca wartość ze źródła danych, wynikowa wartość jest przechowywana w zmiennej lokalnej, która ma typ .NET Framework. `Fill` Dla operacji `DataAdapter` i`Get` metod ,typ.NETFrameworkjestwywnioskowanynapodstawiewartościzwróconejprzezdostawcędanych.NETFramework.`DataReader`  
  
 Zamiast polegać na wywnioskowanym typie danych, można użyć typów metod dostępu typu w `DataReader` przypadku, gdy wiadomo, że określony typ zwracanej wartości. Wpisywane metody dostępu zapewniają lepszą wydajność, zwracając wartość jako określony typ .NET Framework, co eliminuje konieczność stosowania dodatkowej konwersji typu.  
  
> [!NOTE]
> Wartości null dla typów danych .NET Framework dostawcy danych są reprezentowane przez `DBNull.Value`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typu danych serwera SQL](sql-server-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.SqlClient>dla programu.  
  
 [Mapowanie typu danych OLE DB](ole-db-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.OleDb>dla programu.  
  
 [Mapowanie typu danych ODBC](odbc-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.Odbc>dla programu.  
  
 [Mapowanie typu danych Oracle](oracle-data-type-mappings.md)  
 Wyświetla listę odroczonych mapowań typu danych i metod dostępu do danych <xref:System.Data.OracleClient>dla programu.  
  
 [Liczby zmiennoprzecinkowe](floating-point-numbers.md)  
 Opisuje problemy, które deweloperzy często napotykają podczas pracy z liczbami zmiennoprzecinkowymi.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych programu SQL Server i ADO.NET](./sql/sql-server-data-types.md)
- [Konfigurowanie parametrów i typów danych parametrów](configuring-parameters-and-parameter-data-types.md)
- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [System typu wspólnego](../../../standard/base-types/common-type-system.md)
- [Konwertowanie typów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [Omówienie ADO.NET](ado-net-overview.md)
