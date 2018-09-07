---
title: Oracle i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 9a60499674f0192bb7589f227bffb6f907f682d9
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084601"
---
# <a name="oracle-and-adonet"></a>Oracle i ADO.NET
> [!NOTE]
>  Typy w <xref:System.Data.OracleClient> są przestarzałe. Typy w dalszym ciągu obsługiwany w bieżącym of.NET wersji Framework, ale zostanie usunięta w przyszłej wersji. Firma Microsoft zaleca się, że używasz innego dostawcy Oracle.  
  
 W tej sekcji opisano funkcji i zachowań, które są specyficzne dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle zapewnia dostęp do bazy danych Oracle przy użyciu Oracle wywołania interfejsu (OCI), zgodnie z postanowieniami przez oprogramowanie klienckie Oracle. Funkcje dostawcy danych jest bardzo podobny do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server, OLE DB i ODBC.  
  
 Aby użyć [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider Pro Oracle, aplikacja musi odwoływać się do <xref:System.Data.OracleClient> przestrzeni nazw w następujący sposób:  
  
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
 W tym artykule opisano wymagania dotyczące korzystania z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle i opisuje określone problemy, które należy wiedzieć podczas korzystania z niego.  
  
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
 Opisuje bezpiecznego kodowania, korzystając z [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Opisuje sposób tworzenia i używania `DataSets`, wpisane `DataSets`, `DataTables`, i `DataViews`.  
  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 W tym artykule opisano sposób pracy z danymi programu ADO.NET.  
  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 W tym artykule opisano sposób pracy z funkcjami specyficznymi dla programu SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Zawiera opis klas ogólnych, które umożliwiają pisanie kodu niezależnych od dostawcy w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
