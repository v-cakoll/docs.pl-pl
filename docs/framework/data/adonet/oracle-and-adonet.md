---
title: Oracle i ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 381f796bec31bece354001ad46bf5079381d1b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914560"
---
# <a name="oracle-and-adonet"></a>Oracle i ADO.NET
> [!NOTE]
> Typy w <xref:System.Data.OracleClient> są przestarzałe. Typy pozostają obsługiwane w bieżącej wersji of.NET Framework, ale zostaną usunięte w przyszłej wersji. Firma Microsoft zaleca użycie dostawcy Oracle innej firmy.  
  
 W tej sekcji opisano funkcje i zachowania, które są specyficzne dla Dostawca danych .NET Framework dla programu Oracle.  
  
 .NET Framework Dostawca danych dla programu Oracle zapewnia dostęp do bazy danych Oracle przy użyciu interfejsu wywołania Oracle (OCI) dostarczonego przez oprogramowanie klienckie Oracle. Funkcja dostawcy danych została zaprojektowana tak, aby była podobna do .NET Framework dostawców danych dla SQL Server, OLE DB i ODBC.  
  
 Aby użyć dostawca danych .NET Framework dla programu Oracle, aplikacja musi odwoływać się <xref:System.Data.OracleClient> do przestrzeni nazw w następujący sposób:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Podczas kompilowania kodu należy również dodać odwołanie do biblioteki DLL. Na przykład, Jeśli kompilujesz C# program, wiersz polecenia powinien zawierać:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wymagania systemowe](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 W tym artykule opisano wymagania dotyczące korzystania z Dostawca danych .NET Framework dla programu Oracle oraz opisano różne problemy, które należy wziąć pod uwagę podczas korzystania z niego.  
  
 [Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <xref:System.Data.OracleClient.OracleBFile> Opisuje klasę, która jest używana do pracy z typem danych Oracle bInformacje.  
  
 [Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <xref:System.Data.OracleClient.OracleLob> Opisuje klasę, która jest używana do pracy z typami danych LOB firmy Oracle.  
  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Opisuje obsługę typu danych kursora usługi Oracle REF.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Opisuje struktury, których można użyć do pracy z typami danych Oracle, <xref:System.Data.OracleClient.OracleNumber> w <xref:System.Data.OracleClient.OracleString>tym i.  
  
 [Sekwencje Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Opisuje obsługę pobierania wartości sekwencji programu Oracle klucza generowanej przez serwer.  
  
 [Mapowanie typu danych Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Wyświetla listę typów danych Oracle i ich mapowania na <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Transakcje rozproszone Oracle](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Opisuje, jak <xref:System.Data.OracleClient.OracleConnection> obiekt automatycznie jest zarejestrowany w istniejącej transakcji rozproszonej, jeśli określa, że transakcja jest aktywna.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Zawiera opis bezpiecznych praktyk kodowania w przypadku korzystania z ADO.NET.  
  
 [Elementy DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Opisuje sposób tworzenia `DataSets`i używania, `DataTables`wpisywania `DataSets`, i `DataViews`.  
  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Opisuje sposób pracy z danymi w ADO.NET.  
  
 [SQL Server i ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Opisuje sposób pracy z funkcjami i funkcjami, które są specyficzne dla SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Opisuje klasy ogólne, które umożliwiają pisanie kodu niezależnego od dostawcy w ADO.NET.  
  
## <a name="see-also"></a>Zobacz także

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
