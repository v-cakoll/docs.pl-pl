---
title: Oracle i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: d4a86abeca19a0c634d362c1a8a41f5be7346ed7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765792"
---
# <a name="oracle-and-adonet"></a>Oracle i ADO.NET
> [!NOTE]
>  Typy w <xref:System.Data.OracleClient> są przestarzałe. Typy w dalszym ciągu obsługiwany w bieżącym of.NET wersji Framework, ale zostanie usunięta w przyszłej wersji. Firma Microsoft zaleca użycie dostawca programu Oracle innych firm.  
  
 W tej sekcji opisano funkcje i zachowania, które są specyficzne dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu Oracle.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawcy danych programu Oracle zapewnia dostęp do bazy danych Oracle przy użyciu programu Oracle Call Interface (OCI) zgodnie z oprogramowania klienta Oracle. Funkcje dostawcy danych jest bardzo podobny do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server, OLE DB i ODBC.  
  
 Aby użyć [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych dla programu Oracle, aplikacja musi odwoływać się <xref:System.Data.OracleClient> przestrzeni nazw w następujący sposób:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Należy również dołączyć odwołanie do biblioteki DLL podczas kompilowania kodu. Na przykład jeśli są kompilowanie programu C#, powinny zawierać wierszu polecenia:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wymagania systemowe](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 W tym artykule opisano wymagania dotyczące korzystania z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu Oracle i opisano różne problemy pod uwagę podczas korzystania z niego.  
  
 [Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 W tym artykule opisano <xref:System.Data.OracleClient.OracleBFile> klasy, która jest używana do pracy z typem danych Oracle BPLIK.  
  
 [Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 W tym artykule opisano <xref:System.Data.OracleClient.OracleLob> klasy, która jest używana do pracy z typami danych Oracle LOB.  
  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 W tym artykule opisano obsługę typ danych Oracle REF CURSOR.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Zawiera opis struktury, można użyć do pracy z typów danych Oracle, w tym <xref:System.Data.OracleClient.OracleNumber> i <xref:System.Data.OracleClient.OracleString>.  
  
 [Sekwencje Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 W tym artykule opisano obsługę pobierania wartości generowanych przez serwer kluczy sekwencji Oracle.  
  
 [Mapowanie typu danych Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Wyświetla listę typów danych Oracle i ich mapowania <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transakcje rozproszone Oracle](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Opisuje sposób <xref:System.Data.OracleClient.OracleConnection> obiektu automatycznie rejestruje w istniejącej transakcji rozproszonej, gdy ustali, że transakcja jest aktywna.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Opisuje bezpieczne praktyk kodowania, korzystając z [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Opisuje sposób tworzenia i używania `DataSets`, typizowanych `DataSets`, `DataTables`, i `DataViews`.  
  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Opisuje sposób pracy z danymi programu ADO.NET.  
  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Opisuje sposób pracy z funkcjami i funkcje, które są specyficzne dla programu SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Zawiera opis klas rodzajowych, dzięki którym można napisać kod niezależny od dostawcy [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
