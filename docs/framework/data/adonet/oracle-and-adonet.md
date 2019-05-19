---
title: Oracle i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 012a5b55d052f5f06da5c152da79f4676b2bff4e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877949"
---
# <a name="oracle-and-adonet"></a>Oracle i ADO.NET
> [!NOTE]
>  Typy w <xref:System.Data.OracleClient> są przestarzałe. Typy w dalszym ciągu obsługiwany w bieżącym of.NET wersji Framework, ale zostanie usunięta w przyszłej wersji. Firma Microsoft zaleca się, że używasz innego dostawcy Oracle.  
  
 W tej sekcji opisano, funkcji i zachowań, które są specyficzne dla .NET Framework Data Provider for Oracle.  
  
 .NET Framework Data Provider for Oracle zapewnia dostęp do bazy danych Oracle przy użyciu Oracle wywołania interfejsu (OCI), zgodnie z postanowieniami przez oprogramowanie klienckie Oracle. Funkcje dostawcy danych programu zaprojektowano w sposób podobny do tego dostawcy danych .NET Framework dla programu SQL Server, OLE DB i ODBC.  
  
 Aby użyć .NET Framework Data Provider for Oracle, aplikacja musi odwoływać <xref:System.Data.OracleClient> przestrzeni nazw w następujący sposób:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Możesz również musi zawierać odwołanie do biblioteki DLL, podczas kompilowania kodu. Na przykład jeśli kompilujesz program C# powinien zawierać wierszu polecenia:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wymagania systemowe](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Opisuje wymagania dotyczące korzystania z .NET Framework Data Provider for Oracle oraz szereg problemów, które trzeba pamiętać podczas korzystania z niego.  
  
 [Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 W tym artykule opisano <xref:System.Data.OracleClient.OracleBFile> klasy, która jest używana do pracy z typem danych BPLIK Oracle.  
  
 [Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 W tym artykule opisano <xref:System.Data.OracleClient.OracleLob> klasy, która jest używana do pracy z Oracle LOB typów danych.  
  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 W tym artykule opisano obsługę dla typu danych Oracle REF CURSOR.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 W tym artykule opisano struktury, można użyć do pracy z typów danych Oracle, w tym <xref:System.Data.OracleClient.OracleNumber> i <xref:System.Data.OracleClient.OracleString>.  
  
 [Sekwencje Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 W tym artykule opisano obsługę pobierania wartości generowanych przez serwer Oracle sekwencja klucza.  
  
 [Mapowanie typu danych Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Wyświetla listę typów danych Oracle i ich mapowań <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transakcje rozproszone Oracle](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 W tym artykule opisano sposób, w jaki <xref:System.Data.OracleClient.OracleConnection> obiektu pozyskuje automatycznie w ramach istniejącej transakcji rozproszonej, gdy ustali, że jest aktywna transakcja.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Opisuje bezpiecznego kodowania, gdy za pomocą platformy ADO.NET.  
  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Opisuje sposób tworzenia i używania `DataSets`, wpisane `DataSets`, `DataTables`, i `DataViews`.  
  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 W tym artykule opisano sposób pracy z danymi programu ADO.NET.  
  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 W tym artykule opisano sposób pracy z funkcjami specyficznymi dla programu SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Zawiera opis klas ogólnych, które umożliwiają pisanie kodu niezależnych od dostawcy w ADO.NET.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
