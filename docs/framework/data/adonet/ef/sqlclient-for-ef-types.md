---
title: Klient SQL dla typów programu Entity Framework
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: af3a4eea08dd3f4e1a134fcb66d92bc4a3b077c7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248380"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>Klient SQL dla typów programu Entity Framework
Plik manifestu dostawcy programu .NET Framework Dostawca danych for SQL Server (SqlClient) zawiera listę typów pierwotnych dostawcy, zestawów reguł dla każdego typu, mapowania między typami pierwotnymi modelu koncepcyjnego i magazynu oraz podwyższenie i konwersję reguły między typami pierwotnymi modelu koncepcyjnego i magazynu.  
  
 Poniższa tabela zawiera opis typów dla SQL Server 2008, SQL Server 2005 i SQL Server 2000 baz danych oraz tego, jak te typy są mapowane na typy modelu koncepcyjnego. Niektóre nowe typy zostały wprowadzone w nowszych wersjach SQL Server nie są obsługiwane we wcześniejszych wersjach SQL Server. Te typy są wymienione w poniższej tabeli.  
  
|Typ dostawcy<br /><br /> nazwa|Typ dostawcy<br /><br /> atrybuty|`EDMSimpleType`<br /><br /> nazwa|Aspektami|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|n/d|`Edm.Boolean`|n/d|  
|`tinyint`|n/d|`Edm.Byte`|n/d|  
|`smallint`|n/d|`Edm.Int16`|n/d|  
|`int`|n/d|`Edm.Int32`|n/d|  
|`bigint`|n/d|`Edm.Int64`|n/d|  
|`float`|n/d|`Edm.Double`|n/d|  
|`real`|n/d|`Edm.Double`|n/d|  
|`decimal`|n/d|`Edm.Decimal`|Dokładne<br /><br /> Minimalny 1<br /><br /> Długość 38<br /><br /> Wartooć 18<br /><br /> Stałego False<br /><br /> Zasięgu<br /><br /> Minimalny 0<br /><br /> Długość 38<br /><br /> Wartooć 0<br /><br /> Stałego False|  
|`numeric`|n/d|`Edm.Decimal`|Dokładne<br /><br /> Minimalny 1<br /><br /> Długość 38<br /><br /> Wartooć 18<br /><br /> Stałego False<br /><br /> Zasięgu<br /><br /> Minimalny 0<br /><br /> Długość 38<br /><br /> Wartooć 0<br /><br /> Stałego False|  
|`smallmoney`|n/d|`Edm.Decimal`|Dokładne<br /><br /> Wartooć 10<br /><br /> Stałego Prawda<br /><br /> Zasięgu<br /><br /> Wartooć 4<br /><br /> Stałego Prawda|  
|`money`|n/d|`Edm.Decimal`|Dokładne<br /><br /> Wartooć 19<br /><br /> Stałego Prawda<br /><br /> Zasięgu<br /><br /> Wartooć 4<br /><br /> Stałego Prawda|  
|`binary`|n/d|`Edm.Binary`|MaxLength<br /><br /> Minimalny 1<br /><br /> Długość 8000<br /><br /> Wartooć 8000<br /><br /> Stałego False<br /><br /> FixedLength:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda|  
|`varbinary`|n/d|`Edm.Binary`|MaxLength<br /><br /> Minimalny 1<br /><br /> Długość 8000<br /><br /> Wartooć 8000<br /><br /> Stałego False<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`varbinary(max)`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w SQL Server 2000.|n/d|`Edm.Binary`|MaxLength<br /><br /> Wartooć 214748364780<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`image`|n/d|`Edm.Binary`|MaxLength<br /><br /> Wartooć 2147483647<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`timestamp`|n/d|`Edm.Binary`|MaxLength<br /><br /> Wartooć 8<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda|  
|`rowversion`|n/d|`Edm.Binary`|MaxLength<br /><br /> Wartooć 8<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda|  
|`smalldatetime`|n/d|`Edm.DateTime`|Dokładne<br /><br /> Wartooć 0<br /><br /> Stałego Prawda|  
|`datetime`|n/d|`Edm.DateTime`|Dokładne<br /><br /> Wartooć 3<br /><br /> Stałego Prawda|  
|`date`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładne<br /><br /> Wartooć 0<br /><br /> Stałego False|  
|`time`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.Time`|Dokładne<br /><br /> Wartooć 7<br /><br /> Stałego False|  
|`datetime2`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTime`|Dokładne<br /><br /> Wartooć 7<br /><br /> Stałego False|  
|`datetimeoffset`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w SQL Server 2005 i SQL Server 2000.|n/d|`Edm.DateTimeOffset`|Dokładne<br /><br /> Wartooć 7<br /><br /> Stałego False|  
|`nvarchar`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w SQL Server 2000.|n/d|`Edm.String`|MaxLength<br /><br /> Minimalny 1<br /><br /> Długość 4000<br /><br /> Wartooć 4000<br /><br /> Stałego False<br /><br /> Unicode:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`varchar`<br /><br /> Uwaga: Ten typ nie jest obsługiwany w SQL Server 2000.|n/d|`Edm.String`|MaxLength<br /><br /> Minimalny 1<br /><br /> Długość 8000<br /><br /> Wartooć 8000<br /><br /> Stałego False<br /><br /> Unicode:<br /><br /> Wartooć False<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`char`|n/d|`Edm.String`|MaxLength<br /><br /> Minimalny 1<br /><br /> Długość 8000<br /><br /> Wartooć 8000<br /><br /> Stałego False<br /><br /> Unicode:<br /><br /> Wartooć False<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda|  
|`nchar`|n/d|`Edm.String`|MaxLength<br /><br /> Minimalny 1<br /><br /> Długość 4000<br /><br /> Wartooć 4000<br /><br /> Stałego False<br /><br /> Unicode:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda|  
|`varchar`(`max`)|n/d|`Edm.String`|MaxLength<br /><br /> Wartooć 2147483647<br /><br /> Stałego Prawda<br /><br /> Unicode:<br /><br /> Wartooć False<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`nvarchar`(`max`)|n/d|`Edm.String`|MaxLength<br /><br /> Wartooć 1073741823<br /><br /> Stałego Prawda<br /><br /> Unicode:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`ntext`|Równe porównywalne: False<br /><br /> Kolejność porównywalna: False|`Edm.String`|MaxLength<br /><br /> Wartooć 1073741823<br /><br /> Stałego Prawda<br /><br /> Unicode:<br /><br /> Wartooć False<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`text`|Równe porównywalne: False<br /><br /> Kolejność porównywalna: False|`Edm.String`|MaxLength<br /><br /> Wartooć 2147483647<br /><br /> Stałego Prawda<br /><br /> Unicode:<br /><br /> Wartooć False<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
|`Unique`<br /><br /> `identifier`|Równe porównywalne: Prawda<br /><br /> Kolejność porównywalna: Prawda|`Edm.Guid`|n/d|  
|`xml`|Równe porównywalne: False<br /><br /> Kolejność porównywalna: False|`Edm.String`|MaxLength<br /><br /> Wartooć 1073741823<br /><br /> Stałego Prawda<br /><br /> Unicode:<br /><br /> Wartooć Prawda<br /><br /> Stałego Prawda<br /><br /> FixedLength:<br /><br /> Wartooć False<br /><br /> Stałego Prawda|  
  
## <a name="see-also"></a>Zobacz także

- [Specyfikacje CSDL, SSDL i MSL](./language-reference/csdl-ssdl-and-msl-specifications.md)
