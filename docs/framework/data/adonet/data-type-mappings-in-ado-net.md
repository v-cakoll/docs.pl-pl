---
title: Mapowanie typu danych
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 610cdc1a679b0c51125075076120e12db97da421
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980200"
---
# <a name="data-type-mappings-in-adonet"></a>Mapowanie typu danych w ADO.NET
.NET Framework opiera się na wspólnym typie systemu, który definiuje, w jaki sposób typy są zadeklarowane, używane i zarządzane w czasie wykonywania. Składa się z obu typów wartości i typów referencyjnych, które pochodzą z typu podstawowego <xref:System.Object>. Podczas pracy ze źródłem danych typ danych jest wnioskowany od dostawcy danych, jeśli nie został jawnie określony. Na przykład obiekt <xref:System.Data.DataSet> jest niezależny od określonego źródła danych. Dane w `DataSet` są pobierane ze źródła danych, a zmiany są utrwalane w źródle danych przy użyciu `DataAdapter`. Oznacza to, że gdy `DataAdapter` wypełnia <xref:System.Data.DataTable> w `DataSet` z wartościami ze źródła danych, wyniki typów danych kolumn w `DataTable` są .NET Framework typy, a nie typy specyficzne dla dostawcy danych .NET Framework, który jest używany do nawiązywania połączenia ze źródłem danych.  
  
 Podobnie, gdy `DataReader` zwraca wartość ze źródła danych, wynikowa wartość jest przechowywana w zmiennej lokalnej, która ma typ .NET Framework. W przypadku `Fill` operacji `DataAdapter` i `Get` metod `DataReader`typ .NET Framework jest wywnioskowany na podstawie wartości zwróconej przez dostawcę danych .NET Framework.  
  
 Zamiast polegać na wywnioskowanym typie danych, można użyć metod metody dostępu typu w `DataReader`, gdy jest znany konkretny typ zwracanej wartości. Wpisywane metody dostępu zapewniają lepszą wydajność, zwracając wartość jako określony typ .NET Framework, co eliminuje konieczność stosowania dodatkowej konwersji typu.  
  
> [!NOTE]
> Wartości null dla typów danych .NET Framework dostawcy danych są reprezentowane przez `DBNull.Value`.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Mapowanie typu danych serwera SQL](sql-server-data-type-mappings.md)  
 Wyświetla listę wywnioskowanych mapowań typu danych i metod dostępu do danych dla <xref:System.Data.SqlClient>.  
  
 [Mapowanie typu danych OLE DB](ole-db-data-type-mappings.md)  
 Wyświetla listę wywnioskowanych mapowań typu danych i metod dostępu do danych dla <xref:System.Data.OleDb>.  
  
 [Mapowanie typu danych ODBC](odbc-data-type-mappings.md)  
 Wyświetla listę wywnioskowanych mapowań typu danych i metod dostępu do danych dla <xref:System.Data.Odbc>.  
  
 [Mapowanie typu danych Oracle](oracle-data-type-mappings.md)  
 Wyświetla listę wywnioskowanych mapowań typu danych i metod dostępu do danych dla <xref:System.Data.OracleClient>.  
  
 [Liczby zmiennoprzecinkowe](floating-point-numbers.md)  
 Opisuje problemy, które deweloperzy często napotykają podczas pracy z liczbami zmiennoprzecinkowymi.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych programu SQL Server i ADO.NET](./sql/sql-server-data-types.md)
- [Konfigurowanie parametrów i typów danych parametrów](configuring-parameters-and-parameter-data-types.md)
- [Pobieranie informacji o schemacie bazy danych](retrieving-database-schema-information.md)
- [System typu wspólnego](../../../standard/base-types/common-type-system.md)
- [Konwertowanie typów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [Omówienie ADO.NET](ado-net-overview.md)
